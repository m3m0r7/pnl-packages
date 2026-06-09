# cmark Package

Package: `libcmark/libcmark`

Base library: cmark

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libcmark
```

The package requires cmark headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libcmark\Libcmark;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libcmark = $runtime->load(Libcmark::class);

// Convert CommonMark (Markdown) to HTML
$markdown = "# Hello\n\nThis is **cmark** via PHP FFI.\n";
$html     = $libcmark->cmark_markdown_to_html(
    $markdown,
    strlen($markdown),
    0  // options: CMARK_OPT_DEFAULT
);
echo $html;
// Outputs: <h1>Hello</h1>\n<p>This is <strong>cmark</strong> via PHP FFI.</p>\n

// For more control: $libcmark->cmark_parse_document($md, $len, 0)
// then $libcmark->cmark_render_html($node, 0)
```

This snippet is printed when `pnl install libcmark` finishes — it comes from the package's `examples` field in `pnlx.json`.
