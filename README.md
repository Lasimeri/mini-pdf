# mini-pdf

Minimal PDF generator for browsers. Zero dependencies, 5.8KB, CSP-safe.

Generates valid PDF 1.4 documents from plain text with Courier monospace font, automatic word wrapping, and page breaks.

## Usage

```js
import { generatePDF, downloadPDF } from './pdf.js';

// Generate a Blob
const blob = generatePDF('Hello, world!', { title: 'My Document' });

// Trigger a download
downloadPDF('Your text here', 'output.pdf', { title: 'My Paste' });
```

## API

### `generatePDF(text, opts?)`

Returns a `Blob` of type `application/pdf`.

| Parameter | Type | Description |
|---|---|---|
| `text` | `string` | Plain text content |
| `opts.title` | `string?` | PDF metadata title |
| `opts.created` | `string?` | Creation date string |

### `downloadPDF(text, filename?, opts?)`

Triggers a browser file download.

| Parameter | Type | Default | Description |
|---|---|---|---|
| `text` | `string` | | Plain text content |
| `filename` | `string?` | `'paste.pdf'` | Download filename |
| `opts` | `object?` | | Passed to `generatePDF` |

## Specs

- **Format**: PDF 1.4
- **Font**: Courier (built-in, no embedding)
- **Page size**: US Letter (612 x 792 pt)
- **Margins**: 72pt (1 inch) all sides
- **Font size**: 10pt, 14pt line height
- **Encoding**: Latin-1 (non-Latin-1 chars replaced with `?`)

## Performance

| Metric | Value |
|---|---|
| Module size | 5.8 KB (188 lines) |
| 500-line document | ~8ms generation |
| Throughput | ~124 PDFs/sec |
| Output size | ~59 KB for 500 lines |

## Limitations

- Text only (no images, tables, or rich formatting)
- Latin-1 encoding (no CJK, emoji, or extended Unicode)
- Fixed Courier font (no font selection)
- US Letter only (no A4 option)

## License

MIT
