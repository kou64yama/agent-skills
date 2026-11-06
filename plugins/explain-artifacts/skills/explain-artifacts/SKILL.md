---
name: explain-artifacts
description: Explain existing artifacts such as code, changes, documents, and designs in a readable, evidence-based, single-file HTML page. Use when the user wants an HTML explanation of artifacts, with optional SVG diagrams.
---

# Explain Artifacts

Create a self-contained HTML explanation of the requested artifacts. Save it in
a temporary directory and open it in a browser when the environment supports it.

## Establish the facts

Identify the artifacts, intended reader, and explanation goal from the request
and conversation. Inspect the relevant artifacts before describing them. Ask
only when missing context materially changes what should be explained.

Base claims on inspected content or observed behavior. Distinguish what an
implementation does from what documentation says it intends to do. Reading code
does not establish that it has run successfully. Do not invent motivations,
guarantees, results, or relationships. Omit unsupported claims or clearly state
what could not be verified when that limitation matters to the reader.

Keep enough source locations to trace important claims: file paths with line
numbers, document headings, or URLs, as appropriate. For changes, inspect both
the change and enough surrounding context to explain its effect.

## Write the explanation

Use the user's language unless they request another. Lead with what the
artifacts are and the key point the reader should understand. Develop the
explanation in connected, readable paragraphs. Define unfamiliar terms when
needed; use lists, tables, and code excerpts where they improve understanding.

Choose sections to fit the artifacts and audience rather than filling a fixed
report outline. Include source references close to important claims, with a
compact source list when useful. Do not present a local source path as a working
browser link unless the destination is actually accessible there; a readable
path and line number are sufficient.

Add inline SVG only when it clarifies a verified structure, relationship, or
flow. Write a caption stating the point of the diagram, then draw only the
details needed to support it. Give each SVG an accessible title and description,
unique IDs for their references, and a responsive `viewBox`. Keep the explanation
understandable without the diagram.

## Build the single HTML file

Read and adapt [assets/explanation.html](assets/explanation.html). It supplies a
responsive document layout, embedded CSS, and styles for prose, code, tables,
sources, and optional figures. Replace every `{{...}}` placeholder, set `lang`
to the explanation language, and remove unused sample sections and comments.
The template is a starting layout, not a requirement to retain every section.

Keep all rendering resources inside the HTML: inline CSS and SVG, and embedded
images if necessary. Do not require external fonts, stylesheets, scripts, image
files, or a running server. Source links may point outside the file. Static HTML
is normally sufficient.

Escape artifact text inserted into HTML, including code examples, attribute
values, and source labels. Treat artifact markup as text rather than copying it
as executable HTML. Keep long code, paths, and tables usable on narrow screens.

Create a unique directory under the environment's temporary directory, using
`mktemp -d` or an equivalent facility, and write `explanation.html` there as
UTF-8. Use a user-specified destination instead if one was provided. Do not
overwrite the source artifacts or add generated explanations to the repository
unless requested.

## Verify and deliver

Check the explanation against its sources, remove leftover placeholders, and
verify that the HTML has no required external rendering resources. If browser
inspection is available, inspect both a normal and a narrow viewport for
readability, overflow, and diagram legibility. If it is unavailable, check the
file structurally and report that visual verification was not performed.

Open the generated file with an available browser tool or the platform's file
opener (for example, `open` on macOS or `xdg-open` on Linux). Opening the file is
not itself proof of visual verification. If opening is unsupported or fails,
still deliver the saved file; do not keep retrying or introduce hosting solely
to display it.

Return a clickable link to the HTML and a brief description of what it explains.
Mention any material evidence gaps or unperformed verification, and accurately
report whether opening the file succeeded. Keep the temporary output available
for the user.
