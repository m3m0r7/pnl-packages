# libcmark/libcmark examples

```php
use Pnlx\Libcmark\Libcmark;

$libcmark = new Libcmark();

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
