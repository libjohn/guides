# Introduction to Regular Expressions
A Workshop and workbook

Part of the [Data & Visualization Services](http://library.duke.edu/data) -- [Workshop Series](http://library.duke.edu/data/news)  
Meet in the DVS Workshop Room  -- [floor map](http://library.duke.edu/edge/spaces)  
http://v.gd/intro_regex (January 2016)

## Prerequisites
* **You Must Preregister** 
* **Bring YOUR Laptop**

***  **DRAFT  12/22/2015** *** **DRAFT  12/22/2015** *** **DRAFT  12/22/2015**  ***   

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
* All slides and exercises are the intellectual work of the good folks at Intersect
* Slides and exercises are shared with permission
* Please attribute [Intersect](http://www.intersect.org.au/course-resources)

 
---  

## Hands-on

1. Introduction to RegExr.com 
1. Exercises from Intersect Tutorial on Regular Expressions using RegExr
	1. **Exercise 1** -- finding whole words, capitalized words, last words, years, phone numbers, email addresses
		1. **[Open the example RFC text in RegExr](http://www.regexr.com/3c7gi)** 
		2. **Find all literal words**  
		*Simple searches are just like traditional find & replace*
			1. `avian` -- 2 matches   
			<img src="http://www.clipular.com/c/6697213840326656.png?k=Sr4JJIBaQIQrFV_e22vdal35gLk"> &nbsp; &nbsp; <img src="http://www.clipular.com/c/5482778819821568.png?k=0ABAsScKdMlMhm02iRyZaI6HTFo">
			2. `Avian` -- 12 matches
			3. `avian` -- with the ignore case flag -- 14 matches   
			<img src="http://www.clipular.com/c/4523633702600704.png?k=2ANfuhKq9-YlXhHskHO6UWvkeZ0">  &nbsp; &nbsp; <img src="http://www.clipular.com/c/6101324037881856.png?k=6kHKagztUKV9hfLP2f0z64Euk7E">  &nbsp; &nbsp; <img src="http://www.clipular.com/c/5227111764721664.png?k=J7C2jn8BBj9xTRXVugf8d9K2ui0">
			4. Clear the case insensitive flag   
	   
		5. **Find only capitalized** words   
		*Some characters (e.g. " or \[ ) don't have a literal meaning.  They are meta characters*
			1. `[A-Z]\w*` -- character classes \[ \] are denoted by square brackets; wildcards include \* , \+ , ?   
			<img src="http://www.clipular.com/c/4898985692102656.png?k=IPiLHHWl3MWUjXTW0gbaLf5j_pY">
			2. `[A-Z]+` -- match only "all caps" words.  **BUT** this is not quite right.  It doesn't work.  *Do you know why?*
			3. `\b[A-Z]+\b` -- Because you have to match on a word boundary using an anchor class:  \\b
			4. `\b[A-Z]{2,}\b` -- Abbreviations are usually 2 or more upper case characters.  Squiggly brackets \{\} allow for arbitrary repetition   
	   
		6. **Match the last words of sentences**   
		*We can restore a letter's literal meaning by escaping it*
			1. `\w+.` -- This doesn't work because "." matches every character
			2. `\w+\.` -- We escape the period "." with a the escape character \\
			3. `\w+\.\s` -- More precise this time.  Matching on 56 words.  Using \\s allows us to stop matching email address by matching whitespace \\s      
	
		7. **Find all years**   
		*Note the pipe character "\" -- alternation, alternatives.  Note the "()" grouping*   
			1. `\d\d\d\d` -- a lot of matches here
			2. `\d{4}` -- more susccinct but has the same meaning as above
			3. `\b\d{4}\b` -- word boundaries \\b help but there are still some false positives
			4. `\b(19|20)\d\d\b` -- better and works for the twenties and twenty-first centuries   

		8. **Pone numbers**   
		*Note: escape the parenthesis \\\(*   
		*Note: ? indicates optionality matching zero or one occurrence*
			1. `\(\d{3}\) \d{3}-\d{4}` -- Very specific.  This works as long as phone numbers are formatted consistently
			2. `\(?\d+\)? ?[\d-]{5,}\d` -- more permissive
			3. `\(?\d+(\)|.)? ?[\d-.]{5,}\d`	   -- more permissive still.  Allows for \. instead of - as a separator
	   
		9. **Email addresses**
			1. `\w+@[\w\.]+` -- This rule is quite permissive.  It's likely to match some invalid email addresses. e.g. fred@invalid.net   
			It's also likely to miss valid email addresses like luc.small@intersect.org.au   
			**SUGGESTION**: ask the RegExr community:
				1. left-hand sidebar
				2. click Community
				3. search on the term 'email'
				4. From there, I found this one   
				`/([\w\.]+)@([\w\.]+)\.(\w+)/g`   
				Wow!  That saved a lot of time!   
		  
		10. **Section headings**   
		Note how \+ can be applied to a group  
			1. Using the Flag setting of RegExr (upper-left), set to multiline	-- This enables ^ and $ anchors
			2. `^(\w+ ?)+$` -- match repeating words + optional space
			3. Reset the multiline flag   
		
	3. **Exercise 2** -- To die upon a kiss
		1. **Preparation**   
			1. [Open Othello text in a browser window](http://shakespeare.mit.edu/othello/full.html) 
			2. Paste full text into RegExr   
		
		2. **Exploring honesty**
			1. Turn on the case insensitive flag
			2. `honour` -- 14 matches
			3. `honou?r` -- optional "u"  and still 14 matches
			4. `hon(our|ourable|esty?)` -- honour honourable, honest, honesty
			5. Turn off case insensitive flag
		
		3. **Acts and Scenes**
			1. Turn on multiline matching
			2. `^(ACT|SCENE) [IVXLCDM]+` -- literal word, space, roman numerals
			3. turn off multiline matching   

		4. **Major Parts**
			1. Turn on multiline matching
			2. `^[A-Z]+$`
			3. turn off multiline matching   
		
		5. **Questions**
			1. Turn on multiline matching
			2. `^.*\?` -- from start of line to question mark
			3. Turn off multiline matching   
		
	4. **Exercise 3** -- Manipulating captured patterns
		1. **Preparation**
			1. Generate a small list of random names from the [random name generator](http://listofrandomnames.com/)
			2. Click the "List in text area" button, copy and paste the names list to your buffer
			3. Replace the text in the RegExr *Text* panel with the random names
			4. Click the grey *Substitution* bar at the bottom of RegExr
			5. Remove the `\n# $&:\n\t` code in the *Substitution* panel   
			
		2. **Capture and manipulate text**   
		*Notice how $1 and $2 are used to recall the text captured within the parenthesis groupings \(  \)*
			1. `(\w+) (\w+)` -- in the *Expression* panel to highlight all names
			2. `"$&"` -- in the *Substitution* pane will reproduce the text pattern matched within forward slashes (*Expression* pane \/     \/)
			3. `- $2, $1` -- swap the order of the first and last name and precede tha whole name with a dash '-'
			4. `<b>$2</b>, $1` -- Bold the last name and add a coma   
			
	5. **Exercise 4** -- Handling twitter data
		1. **Preparation**
			1. Open this [twitter stream data pre-loaded into RegExr](http://www.regexr.com/3cfee)   
			*Please note this is actual twitter stream data about a politician, the tweets may be offensive*
		2. **Capturing #hashtags, @twitter-handles
			1. `#\w\w+` -- #hastag
			2. `@\w\w+` -- @twitter-handle
			3. `@[A-Za-z]\w+` -- avoids matching times, e.g. @kairos we're meeting for drinks @10   
		
---  

## Thank You for Attending

* **Please** complete the **Feedback Form**
* **Presenter** 
John Little   
Data Management & Data Analysis Consultant   
Data & Visualization Services   
Duke University Libraries   
* **Other Guides & Workbooks**
	* [DVS Guides Page](http://library.duke.edu/data/guides)
	* Workshop/Workbook Guides by John Little
		* [OpenRefine](http://v.gd/openrefine) -- Easy Data Exploration, Data Transformations, Text Normalization, Data Scraping
		* [Web Scraping](http://v.gd/webscrapting) -- Gathering Data from the Web
		* Regular Expressions (RegEx) http://foo.shoegoo.edu  -- Introduction to pattern matching and pattern manipulation



   



