# Documents and Slides from Office Applications

Office applications, such as Microsoft Word and PowerPoint, typically provide a set of reasonably robust accessibility features.
However, these accessibility features may be limited in cloud-based office applications (e.g., Google Docs, Google Slides).

The following sections provide step-by-step instructions to use or enable these accessibility features for common office applications.

## Add Alt Text to Images

For how to write good alt text, please refer to the [](images.md) page. Below are instructions on how to add alt text in some common office applications.

### For Microsoft Word/PowerPoint:

1.  Right-click the image (or a non-text object).
2.  Select `View Alt Text...` from the context menu (sometimes called `Edit Alt Text...`).
3.  Enter the image description in the box. Microsoft Office may offer to generate a description for you; if you use this feature, be sure to review and edit it.
4.  If the image is purely decorative, you can check the `Mark as decorative` checkbox if available. If that option is not available, you can simply say "decorative" in the alt text box.

### For OpenOffice/LibreOffice

1.  Right-click the image (or a non-text object).
2.  Select `Properties` from the context menu (sometimes called `Description`).
3.  Fill in the `Description` Field (sometimes this field is hidden under the `Options` tab). Note that it is the *Description* field that serves as the alt text for the image (not *Title*, *Name*, or, most confusingly, *Alternative*).

### For Google Docs/Slides

1. Right-click the image (or a non-text object).
2. Select `Format options` from the context menu.
3. In the Format options panel that appears on the right, expand the `Alt text` section.
4. Enter the image description in the `Description` field.

### For Apple iWork (Pages/Keynote)

1.  Right-click the image (or a non-text object).
2.  Select `Format` from the context menu.
3.  Enter the image description in the `Description` field.

## Use Semantic Markup

To make your documents screen-reader friendly, use semantic markup to structure your content. Semantic markup tells assistive technologies that a section header is a section header, not just a line of bolded larger text. The steps are similar across different office applications.

1. Typically, you will see in the toolbar a dropdown menu (or a set of buttons) that allow you to select styles (e.g., "Normal", "Paragraph", "Heading 1", "Heading 2", etc.).
2. If you have a section heading, select the text and apply "Heading 1". If you have a subsection heading, apply "Heading 2", and so on.
3. For the regular text, make sure you select "Normal" or "Paragraph" style.
4. You may not like the default formatting of the heading styles. You can modify the styles by doing the following:
    - Select the text and apply the original style first (say you apply "Heading 1").
    - Change the font, size, color, etc. to your liking.
    - Keep the text selected, and go to the Styles menu to find an option called `Update "Heading 1" to Match Selection.` (you may need to hover or right-click on the style name to see this option).
    - This will update the "Heading 1" style to match the formatting you just applied, and all text with "Heading 1" style will be updated accordingly.
    - Repeat the same process for other heading levels as needed.

In addition to headings, also use the built-in list features to create bulleted or numbered lists, rather than manually typing bullets or numbers. This will allow screen readers to recognize the list structure and read it appropriately.

## Use Informative Link Text

If you have any hyperlinks in your document, make sure the link text is informative.

- **DOs**: "my profile," "the accessibility website," "this article on cosmic inflation" etc. If the linked page has an informative title, you can just use that title as the linked text.
- **DONTs**: URL itself, "click here," "read more," "see this," etc.


## Follow the Rules when Using Color

See [](colors.md) for detailed information on the two guidelines: (1) use sufficient contrast and (2) combine color with other indicators.

For example, if you have hyperlinks, it is best practice to keep the underline style so that links are distinguishable from regular text not just by color.


## Use Accessibility Checker

Microsoft Office and OpenOffice/LibreOffice both offer built-in accessibility checkers that can help you check that you have applied the accessibility features correctly and identify any potential issues. To use the accessibility checker:

1. Go to the `Review` tab (in Microsoft Office) or the `Tools` menu (in OpenOffice/LibreOffice) and click `Check Accessibility` (or `Accessibility Check`).
2. Follow the prompts to review any accessibility issues identified by the checker and make necessary adjustments to your document.

Google Docs/Slides and Apple's iWork suite of applications (Pages, Keynote) do not have a built-in accessibility checker unfortunately. If you want to use a checker, you can download the document and then use Microsoft Office or OpenOffice/LibreOffice's accessibility checker.

## Share in the Native File Formats

It may be counterintuitive, but sharing documents and slides in their native file formats (e.g., `.docx`, `.pptx`) can often be more accessible for assistive technologies. If preserving the exact layout is not critical for your use case, consider sharing in the original file format. Or, share it alongside the PDF version.

:::{caution}
If you use Apple's Pages or Keynote, you may want to share in `.docx` or `.pptx` format because Pages and Keynote's native formats are proprietary and require students having access to Apple devices or iCloud to open them.
:::

## Considerations when Saving as PDF

If you must save your documents or slides as PDF files, ensure the accessibility tags are preserved.

1. Find the `Export as PDF` option in your office application.
2. Look for a checkbox or option that says `Document structure tags`, `Tagged PDF`, or `Universal Accessibility PDF/UA`. Make sure it is checked before saving the PDF.

Note that Google Docs and Slides do *not* generate accessible PDFs. See [](google.md) for more details and workarounds.