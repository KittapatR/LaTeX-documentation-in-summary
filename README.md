# LaTeX (*Lay-Tek*) in summary
*Kittapat Ratanaphupha, 24 July 2022 – Present*

This repo provides the KMUTT thesis template, Thai article template and Thai beamer template for Thai users esp. HDS PSCM KMUTT or KMUTT students.

## Here is a thesis format for (CPE/HDS PSCM) KMUTT
https://www.overleaf.com/read/vwtpfxztqgbv

### Here are the available options in the report template

The format is as this in the first line of the document,

```
\documentclass[a4paper, thai, draftreport]{kmuttthesis}
```

`thai`: the report will show in Thai version

`draftreport`: the report will show watermarking as a draft version (when you've done your thesis, you must remove it then.)

`extra`: the report will support **special** annotations for joint degree or its equivalent.

### How to use the report template
1. Click the link I provided above
2. (For non-Overleaf users) Click Menu -> Download: Source
3. (For Overleaf users) Click Menu -> Actions: Copy Project
4. Let's modify it!

### Description of files in the Overleaf project
1. File/folder that you must remain in your computer when you edit your thesis:
1.1. `fonts` folder (embed TH Sarabun New in thesis)
1.2. `Cover.jpg` and `CRA_logo.png` (KMUTT and CRA logo)
1.3. `kmuttthesis.cls` (class file for KMUTT thesis template)
1.4. `main.bib` (placeholder for placing references in thesis)

2. Selective file for typing some thesis

A file name will be like this `main_<language><_hds>.tex`.

`<language>` means what language that thesis will be written in. (THA and ENG)
`<_hds>` means this thesis will be written for HDS student only.

## External links for reference
- https://oeis.org/wiki/List_of_LaTeX_mathematical_symbols (for doing the equations)
- https://latex.codecogs.com/eqneditor/editor.php (for previewing an equation in LaTeX)
- https://www.mathcha.io/ (for doing a figure esp. schematic and mathematical diagram)
- https://www.overleaf.com/learn/latex/Articles/How_to_write_in_Markdown_on_Overleaf (to write markdown in LaTeX)

## Plan for development checklist
(28 July 2022)
- documentation for LaTeXing [Finished: 1/4 parts]

## Done!
- conditional paging for list of figures and list of tables (29 Jul 2022)
- add `PAGE` to every pages in table of contents, list of tables and list of figures.
- watermarking in the full report template when the author would like to have `draftreport` option. (28 Jul 2022)
- Update thai article template (TH Sarabun New is required according to this template; 28 Jul 2022)
- list of symbols and glossaries in the full report template (at first versions)
