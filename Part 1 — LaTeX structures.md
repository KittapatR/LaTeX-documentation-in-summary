# $\LaTeX$ สำหรับคนเพิ่งใช้ชุดที่ 1:<br> โครงสร้างและก่อนที่มันจะเอามาใช้ได้

*กฤตพัฒน์ รัตนภูผา, 24 กรกฎาคม 2565*

ก่อนหน้าที่จะสร้างเอกสารจาก $\LaTeX$ ได้ เราต้องเข้าใจก่อนว่า $\LaTeX$ ทำงานอย่างไรกันแน่ ซึ่งเราเข้าใจกันไปแล้วว่า

- $\LaTeX$ engine ไม่ได้เป็น WYSIWYG (What you see is what you get.) ต้องรันก่อนดูผลลัพธ์ทุกครั้ง
- $\LaTeX$ มีลักษณะคล้าย ๆ HTML หรือ Markdown (Markup languages) ส่วนใหญ่จะมี keyword กำกับเพื่อสร้างความพิเศษให้กับมัน (แต่เราจะพูดต่อในชุดที่ 2 เป็นต้นไป)

แต่นอกจากนี้แล้ว ยังมีเรื่องจุกจิกเล็กน้อยก่อนท่จะทำให้เราสร้างไฟล์ .pdf จาก $\LaTeX$ ได้จะมีอยู่ทั้งสิ้น 3 ประการดังนี้

- [องค์ประกอบโครงสร้างของ $\LaTeX$](#องค์ประกอบโครงสร้างของ-latex) 
    - [Built-in classes ใน $\LaTeX$](#built-in-classes-ใน-latex)
    - [Options ในส่วนเกริ่นนำ](#options-ในส่วนเกริ่นนำ)
    - [ข้างล่าง `\begin{document}` แต่บน `\end{document}`](#ข้างล่าง-begindocument-แต่บน-enddocument)
      - [ลำดับขั้นของ $\LaTeX$ ที่เอาไว้ใช้ในการจัดหัวเรื่องและประเด็น](#ลำดับขั้นของ-latex-ที่เอาไว้ใช้ในการจัดหัวเรื่องและประเด็น)
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
3. `book` เป็นลักษณะคล้าย ๆ รายงานแต่จะมี chapter เหมือน  `report` ซึ่งลักษณะข้อความจะแบ่งชั้นได้ละเอียดกว่า `article` ที่แบ่งได้ถึง `section` เท่านั้น ไม่มี `abstract` แต่มี `frontmatter`, `mainmatter` และ `backmatter` สำหรับการแบ่งเลขหน้าแตกต่างกัน เป็นโรมัน อารบิก และไม่นับหน้าตามลำดับ
4. `beamer` เทียบได้กับ presentation slides สามารถทำ animation ของแต่ละ frame ให้เป็นไปตาม storytelling ของเรา
5. `letter` ไว้ใช้เขียนจดหมายทั่วไปหรือจดหมายแนะนำให้กับนิสิตนักศึกษาที่จะเรียนต่อในระดับบัณฑิตศึกษา

### Options ในส่วนเกริ่นนำ

Options ที่มีใน $\LaTeX$ ที่มักจะนิยมในการเขียน documentclass (Reference: https://texdoc.org/serve/geometry.pdf/0)

- Font size: ปรับขนาดฟอนต์ในการสร้าง document ซึ่งใช้ได้ในทุก documentclass ยกเว้น beamer โดย options ที่ใช้ได้ คือ
  - `10 pt` (default settings)
  - `11 pt`
  - `12 pt`
- Paper size: สิ่งนี้เป็นการปรับหน้ากระดาษ (เช่นกัน beamer ไม่สามารถใช้ได้) ซึ่งจะเป็นไปตามขนาดมาตรฐานต่าง ๆ ดังนี้ [หมายเหตุ: หากว่าอยากปรับหน้ากระดาษใน beamer ให้เปลื่ยนไปใช้ `aspectratio` แทน ซึ่งมี `169, 1610, 149, 54, 43` (default settings) และ `32`] ซึ่งทั้งหมดนี้เป็นขนาดกระดาษที่คุ้นเคยใน Microsoft Word อยู่แล้ว นั่นคือ
  - `letterpaper` (default settings)
  - `legalpaper`
  - `executivepaper` (ทั้งสามแบบ letter, legal และ executive จะเป็นไปตามมาตรฐาน [American loose paper series](https://www.a2-size.com/american-paper-sizes/))
  - `a<number>paper` (The available number is in 0-6. The size is the same as A*X*.)
  - `b<number>paper` (The available number is in 0-6. The size is the same as B*X*.)
  - `c<number>paper` (The available number is in 0-6. The size is the same as C*X*. ซึ่ง A,B,C series จะเป็นไปตามมาตรฐาน [ISO 216](https://en.wikipedia.org/wiki/ISO_216))
  - `b<number>j` (Available number is 0-6. The size is based on JIS B-series.)
  - `ansi<alphabet>paper` (Available alphabet is a-e. The size is based on [ANSI/ASME Y14.1 series](https://en.wikipedia.org/wiki/ANSI/ASME_Y14.1).)
- draft mode `draft` จะให้รูปร่างเป็นแบบร่าง ซึ่งจะไม่แสดงผลภาพให้เห็น จะวางเป็นโครงเพื่อความว่องไวในการ compile ของ $\LaTeX$ เอง (แต่ถ้าหากว่าใช้ option `draft` ใน KMUTT thesis จะเป็นว่าเราจะได้หัวเป็นคำว่า "DRAFT" บนหน้าปกแทน)
- จำนวน columns ใน document ซึ่งจะมี `onecolumn` (default) และ `twocolumn` (หากต้องการมีจำนวนหลักมากกว่า 2 หลัก ให้ใช้ package `multicols` แทน)
- การจัดรูปสมการอาจใช้ `fleqn` (flush left equation: เอาสมการชิดซ้าย), `leqno` (left equation number: เอาตัวเลขสมการไว้ด้านซ้าย) ปกติจะเป็นสมการที่วางอยู่ตรงกลางและเลขสมการอยู่ด้านขวา
- `oneside` และ `twoside` คือ การจัดหน้าแบบพิมพ์หน้าเดียวหรือพิมพ์แบบหน้าหลัง (ซึ่งใน `report` class จะพิมพ์เป็นหน้าเดียวให้ แต่ใน `book` class จะพิมพ์เป็นหน้าหลัง)
- `openany` (default) และ `openright` คือเมื่อเราเปิดบท (`chapter`) ใหม่จะบังคับให้เปิดที่หน้าขวาหรือไม่ อย่างที่เป็นกันในหนังสือทั่วไปก็จะเห็นว่าหน้าแรกของบทต่าง ๆ มักจะอยู่ด้านขวาเสมอ

### เกริ่นนำอื่น ๆ นอกจากการประกาศ documentclass มีอะไรอีกบ้าง

องค์ประกอบของ Preamble ใน $\LaTeX$ มักจะใช้เพื่อนิยามและนำเข้าแพ็กเกจที่ไม่ใช่ build-in methods และ parameters พื้นฐานในระบบ ซึ่งมักจะมี command ดังต่อไปนี้

- `\usepackage[<options>]{<package name>}` หมายถึงเราเอา package ภายนอกที่ไม่มีใน built-in commands มาใช้ เหมือนในภาษา C ที่ทำ `#include<something.h>` หรือภาษา Python ที่ทำ `import some.library` แต่เราสามารถใส่ options ได้เช่นกันขึ้นกับแล้วแต่ package ที่ใช้นั้น ๆ
- `\newcommand{<command name>}[<number of required arguments from 1 to 9>][<default values of optional arguments>]{<value of its command>}` หมายถึงการนิยาม command ใหม่ขึ้นมา ซึ่งอาจจะเป็นประโยชน์ในการจัดหน้าที่ใช้ซ้ำบ่อย ๆ

#### การตั้ง command ใหม่ที่มี input arguments

ในการสร้าง $\LaTeX$ command หนึ่ง ๆ สามารถใช้ static และ dynamic commands ซึ่งใน static command นั้น เราสามารถเขียนได้อย่างง่ายดังนี้

```
\newcommand{<command name>}{<some static result you'd like to get>}
```

เช่นว่า เราต้องการแสดงผล "hello world" ด้วย command `hello` เราสามารถเขียน command ได้ว่า  

- `\renewcommand{<command name>}`

### ข้างล่าง `\begin{document}` แต่บน `\end{document}`

#### ลำดับขั้นของ $\LaTeX$ ที่เอาไว้ใช้ในการจัดหัวเรื่องและประเด็น

การจัดหัวเรื่องและประเด็นใน $\LaTeX$ นั้นมีระดับในการจัดกลุ่มสารเพื่อเล่าเรื่องต่าง ๆ ตามการทำหนังสือ/บทความปกติที่รับทราบกันอย่าง บท (chapter), ตอน (section), ตอนย่อย (subsection) และตอนย่อย ๆ อื่น ๆ ที่ซอยย่อยกว่า subsection (หมายเหตุ: ในบางที การจัดหนังสืออาจมีการเขียนเป็น บรรพ, book หรือภาค) ซึ่งใน $\LaTeX$ นั้นจะมีการจัดที่เฉพาะของมัน มีเพียง 4 ลำดับขั้นดังต่อไปนี้

```
|- chapter (มีเฉพาะใน report และ book)
|  |- section
|     |- subsection
|     |  |- subsubsection
|     |- subsection
|- chapter
```
ซึ่งวิธีการใช้ของมันจะเขียน command ตามที่เขียนไว้ได้เลย เช่น ถ้าเปิด section ใหม่ขึ้นสามารถเขียน

```
\section[<shortened name that display in the ToC>]{<full name that displays in the exactly place>}
```

เช่นว่าเราเขียนว่า `\section[KMUTT]{King Mongkut's University of Technology Thonburi}` หมายความว่า ในหน้าสารบัญจะแสดงให้เห็นเป็น KMUTT แต่ถ้าในหน้าดังกล่าวเมื่อเปิด section จะเขียนเป็น King Mongkut's University of Technology Thonburi ตามด้วยเลข chapter นั้น ๆ ที่ running number มีอยู่

แต่ถ้าเราใส่ asterisk เข้าไป เช่น

```
\chapter*{<placeholder>}
```

ก็จะไม่ใส่เลข chapter เข้าไป กอปรกับไม่แสดงผลในหน้าสารบัญอีกด้วย

## ความแตกต่างของ TeX, XeLaTeX และ LuaLaTeX

## รูปแบบรายงานที่เป็นประโยชน์: report, article และ beamer