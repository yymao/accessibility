# Code Snippets and Software

Here we discuss accessibility best practices when sharing [code snippets](code:snippets),
[Jupyter Notebooks, and MATLAB Live Scripts](code:notebooks).
We also discuss some considerations for [software used in class](code:software).

(code:snippets)=
## Code Snippets

When sharing code snippets, make sure the code is shared in a plain-text format.
Avoid screenshots of code because screen readers cannot read text inside images.

Include comments in the code to explain what the code does and why, and to provide context.
This is a good practice not just for accessibility, as it helps students understand the code better.

(code:notebooks)=
## Jupyter Notebooks and MATLAB Live Scripts

Here's a checklist to make Jupyter Notebooks and MATLAB Live Scripts accessible:

- **Structure the notebook**: Use section headings in your notebooks to organize the content semantically. In Jupyter Notebooks, you can add section headings (`#`, `##`, etc.) in Markdown cells. In MATLAB Live Scripts, you can use the "Section Break" feature to create sections and format headings accordingly.
- **Explain the code**: Don't just show the code; explain what it does and why.
- **Describe plots**: If the notebook generates plots, provide a description of the plot in the Markdown cell immediately following the code cell.
- **Add alt text to images**: If you include images in the notebook, make sure to add alt text to them. In Jupyter Notebooks, you can do this by using the following syntax in a Markdown cell: `![Alt text](image_url)`. In MATLAB Live Scripts, you can add alt text to images by right-clicking the image and selecting "Edit Image..." from the context menu, then entering the alt text in the provided field.

:::{seealso}
You can find more information on [how to use Markdown cells in Jupyter Notebooks](https://jupyter-notebook.readthedocs.io/en/latest/examples/Notebook/Working%20With%20Markdown%20Cells.html) and [how to add headings and alt text in MATLAB Live Scripts](https://www.mathworks.com/help/matlab/matlab_prog/format-live-scripts.html).
:::

(code:software)=
## Software Use in Class

The current requirement focuses on web content and mobile apps, and it does not directly apply to traditional software.
If your class uses software that is not web-based or mobile, you are not required to make the software itself accessible under this requirement.

However, the general ADA requirements still apply. Hence, if a student requests an accommodation related to software use through CDA, you should work with the CDA to ensure the student can access the software and participate in class effectively.

If you post any instructions, guides, or other materials (such as code snippets and notebooks) that are related to the use of software on the course website, you do need to ensure those posted materials are accessible, even if the software itself may not be accessible.
