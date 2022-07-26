# $\LaTeX$ (*Lay-Tek*) สำหรับคนเพิ่งใช้ชุดที่ 1:<br> โครงสร้างและก่อนที่มันจะเอามาใช้ได้

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
      - [ส่วนอื่น ๆ ที่เกี่ยวข้อง](#ส่วนอื่น-ๆ-ที่เกี่ยวข้อง)
    - [เกริ่นนำอื่น ๆ นอกจากการประกาศ class มีอะไรอีกบ้าง](#เกริ่นนำอื่น-ๆ-นอกจากการประกาศ-class-มีอะไรอีกบ้าง)
- [ความแตกต่างระหว่าง pdfLaTeX, XeLaTeX และ LuaLaTeX](#ความแตกต่างของ-pdflatex-xelatex-และ-lualatex)

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

- `\usepackage[<options>]{<package name>}` หมายถึงเราเอา package ภายนอกที่ไม่มีใน built-in commands มาใช้ เหมือนในภาษา C ที่ทำ `#include<something.h>` หรือภาษา Python ที่ทำ `import some.library` แต่เราสามารถใส่ options ได้เช่นกันขึ้นกับแล้วแต่ package ที่ใช้นั้น ๆ ซึ่ง package ที่แนะนำให้ใช้จะเป็น package ที่แนะนำในส่วนที่ 4
- `\newcommand{<command name>}[<number of required arguments from 1 to 9>][<default values of optional arguments>]{<value of its command>}` หมายถึงการนิยาม command ใหม่ขึ้นมา ซึ่งอาจจะเป็นประโยชน์ในการจัดหน้าที่ใช้ซ้ำบ่อย ๆ

#### การตั้ง command ใหม่ที่มี input arguments

ในการสร้าง $\LaTeX$ command หนึ่ง ๆ สามารถใช้ static และ dynamic commands ซึ่งใน static command นั้น เราสามารถเขียนได้อย่างง่ายดังนี้

```
\newcommand{<command name>}{<some static result you'd like to get>}
```

เช่นว่า เราต้องการแสดงผล "hello world" ด้วย command `hello` เราสามารถเขียน command ได้ว่า  

```
\newcommand{hello}{hello world}
```

เราสามารถเรียก command ว่า `\hello` เพื่อแสดงผลว่า "hello world" แต่ถ้าหากว่าอยากให้่แนะนำตัวขึ้นมาได้ใน command `hello` เราสามารถเขียน command ได้ว่า

```
\newcommand{hello}[1]{hello #1}
```

เช่นถ้าเราทำการรัน `\hello{Somchai}` จะได้ออกมาเป็น `hello Somchai` เป็นต้น หรือถ้าหากว่า เราต้องการเขียน optional arguments ลงมาใน command จะสามารถเขียนได้ว่า

```
\newcommand{hello}[1][Somchai]{hello ~#1. #1}
```

หากเราเขียนว่า `\hello[How are you?]` จะได้ออกมาว่า "hello Somchai. How are you?" แต่ถ้าหากเขียนว่า `\hello[World]{How are you?}` จะได้ออกมาว่า "hello world. How are you?" เป็นต้น

- `\renewcommand{<command name>}` จะคล้าย ๆ กับ `newcommand` แต่เพียงแค่ว่าจะใช้ทดแทน command เดิมที่มีอยู่ในสารบบ ซึ่งสามารถทดแทนคำสั่งเดิมที่เป็น built-in command ใน $\LaTeX$ ได้อีกด้วย

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

#### ส่วนอื่น ๆ ที่เกี่ยวข้อง

ส่วนอื่น ๆ เหล่านี้จะเกี่ยวข้องกับการจัด typesetting, equations และ object ต่าง ๆ ที่ผู้เขียนประสงค์จะใส่ เช่น Gantt chart หรือ commutative diagram ก็สามารถนำมาใส่ได้ ซึ่งจะพูดต่อไปในส่วนที่ 2 เป็นต้นไป

![Commutative diagram](images/5_lemma.png)

  > นี่คือ commutative diagram ตามที่กล่าวไว้

## ความแตกต่างของ pdfLaTeX, XeLaTeX และ LuaLaTeX
*(Reference: https://tex.stackexchange.com/questions/13593/the-differences-between-tex-engines)*

แท้จริงแล้ว $\LaTeX$ (Lamport's TeX) และ $\TeX$ เป็นคนละสิ่งกัน ซึ่งความแตกต่างของมันหลัก ๆ คือ การเขียน macro ซึ่งคำสั่ง macro จะหมายถึงการจับกลุ่มของชุดคำสั่งมาใส่เป็นคำสั่งเดียว ซึ่งส่วนที่เป็นประโยชน์และทำให้ $\LaTeX$ สามารถใช้งานได้ง่ายขึ้นเหมือนกับการเขียน markup language อื่น ๆ เช่น cross-reference และ bibliography ซึ่งเป็นส่วนสำคัญที่ทำให้นักวิจัยใช้ $\LaTeX$ มากกว่า $\TeX$ อย่างมีนัยสำคัญ (เขาว่ากันว่า $\TeX$ ตายไปแล้วดังที่ว่านี้)

  > Let us get this straight:  $\LaTeX$  is the modern choice. The successor to Knuth’s $\TeX$ has proven far too useful, far too capable of producing beautiful results with relative ease to be easily supplanted, at least within the foreseeable future.
  >
  > Far and away,  $\LaTeX$  remains the go-to choice for technical communication (e.g. papers, presentations) for many, many people, especially mathematicians and physicists.
  >
  > So no,  $\LaTeX$  is not dead, not by a long shot. In most good math departments, even the undergraduates know  $\LaTeX$. We have websites for discussing math (e.g., Math Overflow) whose editors support  $\LaTeX$. We have MathJax. Hell, even Quora, a website on which the vast majority of writing is non-mathematical, supports  $\LaTeX$ reasonably well, and it has done so for years.
  >
  > **Long live  $\LaTeX$. Long live the queen.**
  >
  > — Joseph Heavner (2019) in Quora

โดยสรุปแล้ว
- pdfTeX เป็น TeX distribution ที่ยอดนิยมซึ่งให้ได้เป็นไฟล์ pdf หรือ dvi (DeVice Independent เป็นไฟล์แบบหนึ่งที่พยายามจัดการ TeX typesetting ซึ่งเป็น output ที่ไม่ขึ้นกับแต่ละเครื่องอย่างที่อาจจะมีการบ่น ๆ กันเมื่อเราใช้ WYSIWYG word processing software)
- LuaTeX เป็น TeX distribution ตัวหนึ่งที่พยายามจะแก้ปัญหาการอ่านอักษรที่เป็น UTF-8 ซึ่งใช้ภาษา Lua ในการรันออกมา
- XeTeX เป็น TeX distribution ที่สามารถใช้ฟอนต์ที่เป็น UTF-8 ได้เช่นกัน ซึ่งสามารถเข้าถึง system fonts ได้เลย โดยไม่ต้องใช้ไฟล์ฟอนต์ (.otf หรือ .ttf เป็นต้น) ในการแสดงผลหน้าจอ

หมายเหตุ: รายงานของเรานั้นแนะนำให้ใช้ XeTeX ด้วยเหตุผลนานาประการ เช่น `polyglossia` package และรายงานของเราจะมีการพิมพ์เป็นภาษาไทยด้วย (คือเราใช้ `fontspec` package) แม้ว่าจะมีความประสงค์จะเขียนรายงานเป็นภาษาอังกฤษ แต่ถ้าหากอยากใช้ LuaTeX อาจจะต้องแก้ไปใช้ `babel` package แทน รวมทั้งการทำ data visualization ใน LuaTeX มีความสวยงามกว่า เมื่อพิจารณา `tikz` หรือ `pdfplots` อาจจะกล่าวได้ว่า

> Features in LuaLaTeX $\supset$ Features in XeLaTeX

- ใครเน้นใช้ความสวยงามของฟอนต์ภาษาไทย ใช้ XeLaTeX
- ใครเน้นใช้ความสามารถพิเศษ ใช้ LuaLaTeX

ส่วน MakeIndex + BibTeX คือ ส่วนที่จัดทำดัชนี (MakeIndex) และบรรณานุกรม (BibTeX) ท้ายเล่ม 