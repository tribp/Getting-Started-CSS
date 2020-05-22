# Getting-Started-CSS

1. Intro

	* BEM notation = Block-Element-Modifier

		* = naming convention for CSS
		    * Block

                ```
				/* Block component */
				.btn {}
                ```
			* Element

                ```
				/* Element that depends upon the block */ 
				.btn__price {}
                ```

			* Modifier
            ```
				/* Modifier that changes the style of the block */
				.btn--orange {} 
				.btn--big {}
            ```
				
		* CSS: where ?
			* Inline
			* between <script> tags in html
			*In separate file .css
		* Start van CSS file: "Universal selector"
			* Problem = normally elements 'inherit properties'. Example: if we set
				□ Body {box-sizing:border-box} -> all decending child elemnts would inherit this, BUT browsers somtimes overwrites it. So better is to address ALL element by '*' !!!!!! 
            ```
			* {
			box-sizing: border-box;
			}
            ```
		
		**Remark:** default = " box-sizing : content-box " -> this feels not natural
			- When 'content-box' -> height - width defines just content so rest must be added and risks to go off screen
			- When 'border-box' -> width-height = border + padding + content
							} WYSIWYG
			
<img src="./img/boxmodel.png" alt="box-model" width="300 px">
			
		○ Display elements: (cfr block-level vs inline elements)
			§ " display : ….. "
				□ display: block :
					® Takes all the available space
					® You can set  margin-top margin-bottom
					® Eg:<div> <nav>  <h1> <p> …
				□ displa: inline:
					® Takes only the space they need
					® margin-top /bottom han NO effect
					® Padding has different effect
					® Eg: <a> <span><img>
				□ display: inline-block 
					
				□ display: none
					® Removes element from document
					® Other elements will move and take its space
					® Remark:
						◊ Visibility:hidden
							} Will remain and holds its place but not visible
		○ Margin colapsing
<img src="./img/marginCollapse.png" alt="margin collapse" width="400px">
		○ Specificity:
		○ Pseudo Class - Pseudo Element
		Zie MDN

<img src="./img/pseudoClasses.png" alt="margin collapse" width="400px">
		○ 
		Vb:
			- Pseudo class:
				□ li:hover -> om van kleur te wijzigen bvb in navbar
				□ :focus :active etc -> zie MDN
			- Pseudo element:
				□ p::first-letter -> om eerste letter van p te stylen zoals in krant
		○ Combining multiple rules (different than colmbinators!)
		
			.main-nav__item a:hover,
			.main-nav__item a:hover{
			color:#aaaaaa;
			}
		○ Difference: :hover   :focus   :active
			- Remember: a computer has many input devices!
			
				□ Hover:
					® Time when mouse is over elemnt
					® ! Do not use hover on mobile devices-> get stuck!
					
				□ Focus:
					® When element has 'focus' -evident :-)
						◊ = at the moment button is clicked
						◊ Eg: input text field can have focus while hovering with mouse over other elements
					® ! Geeft "blauwe" 'outline -> kunnen dit afzetten met onderstaande
						◊ Outline = maakt geen deel uit van box-model!
						(cfr afmetingen)
					
						.button:focus{
						outline:none;
						}
						
				□ Active:
					® Time when pressing button down.
	2. Hierarchy:
	• <html>
		○ <body>
			- <main>
				□ <element>
		If we set "height:100%" -> 100% refers to 'parent'. So if nothing is set at parrent it will be 100% of nothing. 
		○ When refering to the total page -> we need to go and chain upto <html>. If set height:100% at this level, it will refer to the full page and a child set at 50% wil take 50% height of screen.

**Summary:**

<img src="./img/properties2remember.png" alt="margin collapse" width="400px">

	• !important -> do NOT use it -> bad coding (all over the place!!)
	Goal = it overwrites all other 'specificity' -> will lead to more !important :-(
		h1 { 
		color: red !important;
		}
	1. Positioning
	
	- 'position':
		○ Static = default -> according to document flow.
		○ 'fixed':
			- Element comes out of document flow -> does not exist for other elements
			- Context reference = viewport
			- A block element becomes 'inline-blox'
			- Now we can use 
				□ 'top:…' 
				□ 'bottom:…'
				□ 'left:…'
				□ 'right:…' 
					® To position element on screen
					® Mostly used to fix a top navigation bar
					® Remark: use box-sizing:border-box in case of problem with borders!
			- Z-index:
				□ 'auto' (default and = 0)
				□ Value greater than will position it on top, smaller will be below
					® Eg: 'z-index: -1' ->will position it under cfr background image
		○ 'absolute'
			- Element komt los uit document flow
			- If no parent has a position property -> html box is the context
			- If a parent element has: 'position:relative'
				□ -> this parent is the reference context
		○ 'relative'
			- Element blijft IN documentflow
			- Element verschuift tov zijn originele plaats
		
		Remark: In case you want to hideyour element once is start going out of the parent:
Overflow:hidden (on the parent)