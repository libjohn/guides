# Introduction to Regular Expressions
A Workshop and workbook

Part of the [Data & Visualization Services](http://library.duke.edu/data) -- [Workshop Series](http://library.duke.edu/data/news)  
Meeti in the DVS Workshop Room  -- [floormap](http://library.duke.edu/edge/spaces)  
http://url.io/regex  

## PreRequisites
* **You Must Preregister** 
* **Bring YOUR Laptop**

***  **DRAFT  12/22/2015**  **DRAFT  12/22/2015**  **DRAFT  12/22/2015**  ***   

--------

## Outline
* Data & Visualization Services
 * Who We Are
* This workshop is **completely based on the good work from [Intersect](http://www.intersect.org.au/course-resources)** in Australia
 * Presentation:  Slides from the [Intersect Slide Deck](http://www.intersect.org.au/course-resources)
 * Exercises:  Based on slides 15-18
* Hands-on
 * Introduction to RegExr
 * Exercises
* Closing
 * Feedback Form
 * Go forth making expressions and finding patters with regularity

---
 
## Regular Expressions -- an Introduction
* [Slides 3-13](/regex/Intersect PDF Materials/Slides.pdf) from [Intersect](http://www.intersect.org.au/course-resources)
 
---  

## Hands-on

1. Introduction to [RegExr](http://regexr.com)
1. Exercises from Intersect Tutorial on Regular Expressions using RegExr
 2. Exercise 1 -- finding whole words, capitalized words, last words, years, phone numbers, email addresses
    3. [Open the example RFC text in RegExr](http://www.regexr.com/3c7gi) 
    4. **Find all literal words**  
	*Simple searches are just like traditional find & replace*
       1. `avian` -- 2 matches   
	   <img src="http://www.clipular.com/c/6697213840326656.png?k=Sr4JJIBaQIQrFV_e22vdal35gLk"> &nbsp; &nbsp; <img src="http://www.clipular.com/c/5482778819821568.png?k=0ABAsScKdMlMhm02iRyZaI6HTFo">
       2. `Avian` -- 12 matches
       3. `avian` -- with the ignore case flag -- 14 matches   
	   <img src=http://www.clipular.com/c/4523633702600704.png?k=2ANfuhKq9-YlXhHskHO6UWvkeZ0>  &nbsp; &nbsp; <img src=http://www.clipular.com/c/6101324037881856.png?k=6kHKagztUKV9hfLP2f0z64Euk7E>  &nbsp; &nbsp; <img src=http://www.clipular.com/c/5227111764721664.png?k=J7C2jn8BBj9xTRXVugf8d9K2ui0>
       4. Clear the case insenstive flag
    5. **Find only capitalized** words   
	*Some characters (e.g. " or \[ ) don't have a literal meaning.  They are meta characters*
	   1. `[A-Z]\w*` -- character classes \[\] are denonted by square brackets; wildcards include \* , \+ , ? 
	   2. `[A-Z]+` -- match only "all caps" words.  **BUT** this is not quite right.  It doesn't work.  *Do you know why?*
	   3. `\b[A-Z]+\b -- Because you to match on a word boundary using an anchor class.  This allows you to match the whole word.
 3. Exercise 2
 4. Exercise 3
 5. Exercise 4

---  

## Thank You for Attending

* **Please** complete the **Feedback Form**
* **Presenter**
**John.Little@Duke.edu**   
Data Management & Data Analysis Consultant   
Data & Visualization Services   
Duke University Libraries   
* **Other Guides & Workbooks**
 * [DVS Guides Page](http://library.duke.edu/data/guides)
 * Workshop/Workbook Guides by John Little
  * [OpenRefine](http://v.gd/openrefine) -- Easy Data Exploration, Data Transformations, Text Normalization, Data Scraping
  * [Web Scraping](http://v.gd/webscrapting) -- Gathering Data from the Web
  * Regular Expressions (RegEx) http://foo.shoegoo.edu  -- Introduction to pattern matching and pattern manipulation



   




