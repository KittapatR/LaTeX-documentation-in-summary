# $\LaTeX$ สำหรับคนเพิ่งใช้ชุดที่ 1: โครงสร้างและก่อนที่มันจะเอามาใช้ได้

*กฤตพัฒน์ รัตนภูผา, 24 กรกฎาคม 2565*

ก่อนหน้าที่จะสร้างเอกสารจาก $\LaTeX$ ได้ เราต้องเข้าใจก่อนว่า $\LaTeX$ ทำงานอย่างไรกันแน่ ซึ่งเราเข้าใจกันไปแล้วว่า

- $\LaTeX$ engine ไม่ได้เป็น WYSIWYG (What you see is what you get.) ต้องรันก่อนดูผลลัพธ์ทุกครั้ง
- $\LaTeX$ มีลักษณะคล้าย ๆ HTML หรือ Markdown (Markup languages) ส่วนใหญ่จะมี keyword กำกับเพื่อสร้างความพิเศษให้กับมัน (แต่เราจะพูดต่อในชุดที่ 2 เป็นต้นไป)

แต่นอกจากนี้แล้ว ยังมีเรื่องจุกจิกเล็กน้อยก่อนท่จะทำให้เราสร้างไฟล์ .pdf จาก $\LaTeX$ ได้จะมีอยู่ทั้งสิ้น 3 ประการดังนี้

- [องค์ประกอบโครงสร้างของ $\LaTeX$](#องค์ประกอบโครงสร้างของ-latex) 
    - [Built-in classes ใน $\LaTeX$](#built-in-classes-ใน-latex)
    - [Options ในส่วนเกริ่นนำ](#options-ในส่วนเกริ่นนำ)
    - [ข้างล่าง `\begin{document}` แต่บน `\end{document}`](#ข้างล่าง-begindocument-แต่บน-enddocument)
    - [เกริ่นนำอื่น ๆ นอกจากการประกาศ class มีอะไรอีกบ้าง](#เกริ่นนำอื่น-ๆ-นอกจากการประกาศ-class-มีอะไรอีกบ้าง)
- [ความแตกต่างระหว่าง TeX, XeLaTeX และ LuaLaTeX](#ความแตกต่างของ-tex-xelatex-และ-lualatex)
- [รูปแบบรายงานที่เป็นประโยชน์: report, article และ beamer](#รูปแบบรายงานที่เป็นประโยชน์-report-article-และ-beamer)

## องค์ประกอบโครงสร้างของ $\LaTeX$

ลักษณะโครงสร้างทั่วไปของ LaTeX script (ซึ่งอยู่ในสกุล .tex) จะมีดังต่อไปนี้

```
\documentclass[<options>]{<class>}
.
.
.
<preamble> # packages, settings
.            and configurations
.            will be here.
.
\begin{document}
.
.
<contents> # contents in the article
.            will be here.
.
\end{document}
```

### Built-in classes ใน $\LaTeX$

ซึ่ง class ที่มักใช้ใน $\LaTeX$ ทั่วไปที่ไม่มี customized class ขึ้นมีดังต่อไปนี้

1. `article` มักจะใช้ในการเขียนบทความขนาดสั้นจำพวกโน้ตและบทความวิจัย
2. `report` มักจะใช้เขียนวิทยานิพนธ์และรายงานสรุปโครงการที่ต้องการหน้าปกและโครงสร้างบทนำ (ซึ่งรายงานโปรเจกต์จบจะเขียนภายใต้รูปแบบนี้ ซึ่งเขียนคลาสพิเศษว่า `kmuttthesis` อย่างที่เคยเกริ่นไปแล้วว่ามี options อย่างไรบ้าง)
3. `book` เป็นลักษณะคล้าย ๆ รายงานแต่จะมีเป็น chapter ซึ่งลักษณะข้อความจะแบ่งชั้นได้ละเอียดกว่า `report` และ `article`
4. `beamer` เทียบได้กับ presentation slides สามารถทำ animation ของแต่ละ frame ให้เป็นไปตาม storytelling ของเรา
5. `letter` ไว้ใช้เขียนจดหมายทั่วไปหรือจดหมายแนะนำให้กับนิสิตนักศึกษาที่จะเรียนต่อในระดับบัณฑิตศึกษา

### Options ในส่วนเกริ่นนำ

Options ที่มีใน $\LaTeX$ ที่มักจะนิยมในการเขียน documentclass

- Font size: ปรับขนาดฟอนต์ในการสร้าง document ซึ่งใช้ได้ในทุก documentclass ยกเว้น beamer โดย options ที่ใช้ได้ คือ
  - `10 pt` (default settings)
  - `11 pt`
  - `12 pt`
- Paper size: สิ่งนี้เป็นการปรับหน้ากระดาษ (เช่นกัน beamer ไม่สามารถใช้ได้) ซึ่งจะเป็นไปตามขนาดมาตรฐานต่าง ๆ ดังนี้ [หมายเหตุ: หากว่าอยากปรับหน้ากระดาษใน beamer ให้เปลื่ยนไปใช้ `aspectratio` แทน ซึ่งมี `169, 1610, 149, 54, 43` (default settings) และ `32`]
  - `letterpaper` (default settings)
  - `a4paper`
  - `b5paper`
  - `legalpaper`
- 

### เกริ่นนำอื่น ๆ นอกจากการประกาศ documentclass มีอะไรอีกบ้าง

องค์ประกอบของ Preamble ใน $\LaTeX$ มักจะใช้เพื่อนิยามและนำเข้าแพ็กเกจที่ไม่ใช่ build-in methods และ parameters พื้นฐานในระบบ ซึ่งมักจะมี command ดังต่อไปนี้

### ข้างล่าง `\begin{document}` แต่บน `\end{document}`

## ความแตกต่างของ TeX, XeLaTeX และ LuaLaTeX

## รูปแบบรายงานที่เป็นประโยชน์: report, article และ beamer