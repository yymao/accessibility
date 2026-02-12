# Webpages (HTML)

Drafting content directly in HTML (or using a content management system that generates HTML) is one of the best ways to ensure accessibility, provided you follow standard web practices.

## Add Alt Text to Images

Include the `alt` attribute in every `<img>` tag: `<img src="..." alt="Description of the image">`.

For how to write good alt text, please refer to the [](images.md) page.

## Use Semantic HTML Tags

HTML offers elements that describe the role of the content they contain. Using these correctly allows screen readers to navigate the page meaningfully.

-   **Headings**: Use `<h1>` through `<h6>` to outline the document structure. Do not skip levels (e.g., do not jump from `<h1>` to `<h3>`).
-   **Lists**: Use `<ul>` for unordered (bulleted) lists and `<ol>` for ordered (numbered) lists.
-   **Regions**: Use tags like `<nav>`, `<main>`, `<header>`, and `<footer>` to define page regions.

## Use Informative Link Text

If you have any hyperlinks in your document, make sure the link text is informative.

- **DOs**: "my profile," "the accessibility website," "this article on cosmic inflation" etc. If the linked page has an informative title, you can just use that title as the linked text.
- **DONTs**: URL itself, "click here," "read more," "see this," etc.

## Follow the Rules when Using Color

See [](colors.md) for detailed information on the two guidelines: (1) use sufficient contrast and (2) combine color with other indicators.

For example, if you have hyperlinks, it is best practice to keep the underline style so that links are distinguishable from regular text not just by color.

## Use MathJax for Math Content

Render math using MathJax rather than images of equations. This allows screen readers to read the math semantically, and also allows you to simply write equations in LaTeX. It's really a win-win. Using MathJax is also straightforward. See below for an example:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>MathJax example</title>
  <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@4/tex-mml-chtml.js"></script>
</head>
<body>
<p>
  When \(a \ne 0\), there are two solutions to \(ax^2 + bx + c = 0\) and they are
  \[x = {-b \pm \sqrt{b^2-4ac} \over 2a}.\]
</p>
</body>
</html>
```

## Use Accessibility Checker

You can use an accessibility checker tool to check your webpage for accessibility issues and get suggestions on how to fix them.
You can find a list of accessibility checker tools at W3C's [Web Accessibility Evaluation Tools List](https://www.w3.org/WAI/test-evaluate/tools/list/).
A few popular options include:

- [](https://www.accessibilitychecker.org/)