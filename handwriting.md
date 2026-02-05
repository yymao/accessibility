# Handwritten Notes

:::{note}
As of February 5, 2026, the CTE's [Accessibility Essentials page](https://cte.utah.edu/instructor-education/accessibility-essentials/index.php#access5) states that "instructors can continue to provide "as-is" images/PDFs of handwritten notes, *but only under certain circumstances*."
Specifically, the allowed circumstance is when all the following are met: the class is an in-person class, the materials in the handwritten notes are covered in other course resources, *and* the notes are provided only as a record of what was discussed in class.
The CTE also states that they are "working to find further legal guidance on this question to ensure we provide the most accurate information possible."
:::

Handwritten notes (e.g., scanned lecture notes, tablet annotations, pictures of board writing) present significant accessibility challenges because they are not machine-readable.
This is not to say that handwritten notes should be avoided completely, but it is important to consider their role in your instruction, and identify ways to make the content, not necessarily the handwriting itself, accessible to all students.


## Consider How the Handwritten Notes Serve Your Students

Consider a student who is not able to access the handwritten notes. Will the student still be able to learn the same content, without significant disadvantage, as a student who can access the handwritten notes? This is the key question to ask as we think about the accessibility of handwritten notes.

For example, if the content of the handwritten notes is already covered in other accessible course materials (e.g., a textbook), you can share the handwritten notes with an additional note to point the students to where they can find the content in other accessible course materials. In this case, students who cannot access the handwritten notes can still learn the same content as students who can access the handwritten notes.

If, on the other hand, the handwritten notes are essential for students to learn certain content, then it becomes important to provide an accessible version of the handwritten notes.

## Use AI to Convert Handwritten Notes to Accessible PDF

With the help of modern AI tools, it is possible to convert handwritten notes into an accessible PDF file without too much manual work. For example, you can use the U's ChatGPT subscription to convert handwritten notes into a LaTeX source file using the following prompt (edit the context as needed):

> Generate a LaTeX source file that captures all the contents of the uploaded handwritten lecture notes. Make the LaTeX file reflect the handwritten notes as closely as possible. Context: The lecture notes are for an undergraduate-level course on cosmology. This particular lecture discusses solving the scale factor for single-component universes.

:::{tip}
Use the flagship/pro version of ChatGPT for better results. The free version may not be able to handle the task well.
:::

Once you have the LaTeX source file, you will want to review it and also add the `\DocumentMetadata` tags as described in [](latex.md) to make it an accessible PDF file.
