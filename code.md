# Code Snippets and Jupyter Notebooks

This page covers some accessibility best practices when sharing code snippets and Jupyter Notebooks.

## Code Snippets

When sharing code snippets in documents or on the web, share them in text format.
Avoid screenshots of code because screen readers cannot read text inside images.

Include comments in the code to explain what the code does and why and to provide context.
This is a good practice not just for accessibility as it helps students understand the code better.

## Jupyter Notebooks

Jupyter Notebooks are a popular format for coding and data analysis. To make them accessible:

- **Structure with Markdown**: Use Markdown cells to provide structure and context. Use headings (`#`, `##`, etc.) to organize the content semantically.
- **Explain the code**: Don't just show the code; explain what it does and why.
- **Describe plots**: If the notebook generates plots, provide a description of the plot in the Markdown cell immediately following the code cell.
- **Add alt text to images**: If you include images in the notebook, make sure to add alt text to them. In Jupyter, you can do this by using the following syntax in a Markdown cell: `![Alt text](image_url)`.
