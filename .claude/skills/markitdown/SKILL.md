---
name: markitdown
description: >
  Convert any file to clean Markdown using Microsoft MarkItDown. Supports PDF, Word (.docx), Excel (.xlsx),
  PowerPoint (.pptx), images (with OCR/alt-text), audio (transcription), HTML, ZIP archives, YouTube URLs,
  Wikipedia pages, and more. Use when the user wants to extract text from a document, convert a file to
  Markdown, or process mixed content for LLM ingestion.
---

# MarkItDown

Microsoft's open-source tool that converts virtually any file format into clean, LLM-ready Markdown.

## Supported Input Formats

| Format | Notes |
|--------|-------|
| PDF | Text extraction |
| Word (.docx) | Full document structure |
| Excel (.xlsx) | Tables → Markdown tables |
| PowerPoint (.pptx) | Slides → Markdown sections |
| Images (.jpg, .png, .gif, .webp) | Alt-text / EXIF / optional LLM description |
| Audio (.mp3, .wav) | Speech-to-text transcription via Azure/OpenAI |
| HTML | Cleans and extracts readable content |
| CSV / TSV | Tables → Markdown |
| ZIP | Recursively converts all contained files |
| YouTube URLs | Extracts transcript and metadata |
| Wikipedia URLs | Extracts article content |
| EPub | eBook extraction |

## Installation (Windows / PowerShell)

```powershell
pip install markitdown[all]
# Or for specific features:
pip install markitdown          # base
pip install markitdown[pdf]     # PDF support
pip install markitdown[docx]    # Word support
pip install markitdown[pptx]    # PowerPoint support
```

## Usage

### CLI
```powershell
markitdown archivo.pdf                    # → imprime Markdown en consola
markitdown archivo.pdf -o salida.md       # → guarda en archivo
markitdown archivo.docx -o salida.md
markitdown "https://youtube.com/..."      # → transcribe vídeo de YouTube
markitdown imagen.jpg                     # → extrae texto/alt-text
```

### Python API
```python
from markitdown import MarkItDown

md = MarkItDown()

# Desde archivo
result = md.convert("documento.pdf")
print(result.text_content)

# Desde URL
result = md.convert("https://en.wikipedia.org/wiki/Python_(programming_language)")
print(result.text_content)

# Desde stream
with open("archivo.xlsx", "rb") as f:
    result = md.convert_stream(f, file_extension=".xlsx")
    print(result.text_content)
```

### Con descripción de imágenes via LLM
```python
from markitdown import MarkItDown
from openai import OpenAI

client = OpenAI()
md = MarkItDown(llm_client=client, llm_model="gpt-4o")
result = md.convert("imagen.jpg")
print(result.text_content)  # Incluye descripción generada por IA
```

## Workflow típico con agentes IA

1. El usuario tiene documentos (PDFs, Word, Excel) que quiere procesar con IA
2. Usa MarkItDown para convertirlos todos a Markdown
3. Los archivos .md resultantes se pueden subir directamente a Claude Projects, Antigravity o cualquier LLM
4. El LLM puede entonces analizar, resumir, comparar o extraer datos

## Integración como MCP Server

```json
{
  "mcpServers": {
    "markitdown": {
      "command": "uvx",
      "args": ["markitdown-mcp"]
    }
  }
}
```

Esto permite a Claude Desktop convertir archivos directamente usando la herramienta convert_to_markdown.

## Notas de seguridad

- MarkItDown opera con los permisos del proceso actual
- En entornos no confiables, usa convert_stream() o convert_local_file() en vez de convert(url)
- Sanitiza inputs antes de procesar archivos de usuarios desconocidos