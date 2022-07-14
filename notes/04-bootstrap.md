# Bootstrap

<!-- NOTE link to bootstrap CSS only -->
CSS Only:
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous">

Put is style.css AFTER bootstrap link so that style.css can override bootstrap styles

<!-- NOTE Javascript bootstrap bundle -->
Javascript bundle goes in the BOTTOM of the body tag - it takes the longest to load/render so it goes at the bottom so that the page loads first



-bs5$ : to quick insert bootstrap style sheet and bootstrap javascript 
! : quick insert doctype (then copy CDN for CSS)

<style.debug> : Codeworks snippet for VSCode 
- applies outline visibility for boxes 
- targets the body with a class debug (class="debug" needs to be put on body)

body.debug *(all) [class*='col-']
}

Nesting:
<Main> container
    <Section> Row
        <Div> Column
        <Div> Column
    <Section> Row
        <Div> Column 

** a container holds a row (which is a flexbox), the row holds a column

Container 
- holds the other content of bootstrap (rows and columns)
    - container-fluid = 100% of the page  
    - container = has built in padding and margin 

Rows 
- ARE display flex
- can have multiple rows in a container

Column 
= take up percentage of the page
- exist in rows 
- can have multiple columns (up to 12) in a row
- ARE NOT display flex
- RULE: there can only be 12 column across the page 
- Different size columns =
        .col-1  = class="col-1"
        .col-2  = class="col-2"
        .col-3 etc. 
            *** column numbers need to add to 12 (i.e. col-4 and col-8 OR col-6 and col-6)
            *** if it goes over 12 it will wrap it under the other columns in the next level
            *** columns sizes are based on the size of the row 

p-1: bootstrap padding tag (comes in different sizes)
m-1: bootstrap margin tag (comes in different sizes)

<!-- NOTE moving stuff left/right -->
1) To move columns within a row = add extra blanks columns 
2) offset-# = creates margin empty space 
    offset-3 = creates col-3 of space 
    *** has to be a whole number (1-12) because the numbers exist in a style sheet and are a CLASS
    <DIV> col-1 offset-3
        *** offset goes before the column 
    <!-- NOTE important for moving stuff around  -->
        *** parent will set the layout of the children 
    - justify-content-SPACE
    -   using justify-content-center put into section when you want to move the div inside 

<!-- SECTION Styles - can find on bootstrap website -->
Colors
- bg-COLOR (theme colors that we have access too)
    -bg-warning 
    -bg-primary 
    -bg-secondary etc. 

<!-- NOTE left or right padding/margin on the container (rows are iffy sometimes) -->
Padding
- p-# 
- use x or y for left and right 
    - px-2 = padding on the left for 2 space
    - py-2 = padding on the right for 2 spaces
- not in em (use CSS to change padding to em)

Margin
- m-#

Text Color
- text-COLOR

Fonts
- fw-STYLE/WEIGHT/ETC. 

Insert image into CSS
.hero-image{
    background-image: url(copy and paste URL)
    background-size: cover 
        - covers the entire background 
    height: 100vh will cover the entire page
}

img-fluid 
- make the image fit the container (don't be bigger than the parent container)

putting a row in the column 
- divides the column and puts 12 more columns inside 

<!-- NOTE not common - try not to use this -->
when you don't supply a size for the col
- the columns will try to share the space of the row evenly 

Breakpoints 
- on bootstrap website 
- class will apply at a specific screen size 
<!-- NOTE webpage to smaller screen -->
- Shrinking screen and keeping paragraph the same size
    *** col-12 (then on medium screens) col-md-7
    *** go left to write: col-12 col-sm-10 col-md-8 
    <!-- NOTE do this -->
        - use two different sizes for mobile responsiveness (desk format(md) and mobile format)
- can put screen size on padding 
- WILL NOT work on colors: cannot do text-light text-md-dark 

<!-- NOTE keybinding stuff highlight + cmd 'd' :to highlight and change everything -->

Buttons going to part of the page 
- make <a> tag 
- make <href "#about"> will let you go to about section 
- add id (#about) on the section/div

<!-- NOTE nav bar top style -->
fix-top - will keep the nav bar at the top of the page
    - will need to add padding to whatever is under it
sticky-top - will stick to the parent and will no longer stick if you scroll to a new parent
    - but can stick to body and it will stay on the page the entire time
    - does not cut off space




<!-- REVIEW review these topics  -->
sizing a column 
- setting a height 
vh: view height 
OR
setting the size of the row 

img-fluid : goes on img tag itself

spacing rows: not using all 12 units use display flex: space-around 

rows already have d-flex on it 

align-self : is on one object 

<!-- NOTE notes on FIGMA -->
FIGMA:

- kind of like ms paint 
- creates a "High fidelity" prototype 
    - "Wire frame" creates just boxes and makes space (no content)

- start with frame (to represent a single page of application)
- pick a frame for the correct display (desktop, phone, etc)
- make a component 
    - boxes (nav bar, main)
    - CHALLENGE: make sure to keep heirarchy in order (how are you going to layout HTML)
    - fill colors to differentiate (coolers color generator)
        - make boxes off to the side to put in color pallet and save it (create color and name it)
        - font 36 is h1 
        - limit crazy fonts to titles/logo - use normal fonts in paragraphs 
            - consider contrast, readability, etc. (make things acessability for people with disabilities)
        - dont use pure white or pure black 
- add extensions for plug ins (material design icons)
- cmd 'g' to make a group 
- make a component 
    - effects will apply across other duplicated components
- can add functionality 
    - prototype 
    - create frame 
        - frames can make things interactive 


<!-- NOTES 7/14 -->
Building mock from Figma 

create an assets folder
    -put style.css in there 
    - put in images 


<!-- NOTE -->
attributes with header/footer

body{
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

main{
    flex-grow: 1;
    <!-- NOTE making extra space for initial layout - bringing the footer to the bottom -->
}


cmd + 'd' to highlight all the same element 

<!-- NOTE how to switch content based on screen size -->
<!-- REVIEW -->
Desktop screen (hidden on mobile, shown on desktop (md))
d-none = 
d-md-block = 

Mobile screen
d-md-none = 

md screen and above use block 


<!-- NOTE -->
white text with a drop shadow = the easiest to read over most images 
.text-shadow{
    text-shadow: 1px 1px 10px black;
}

<!-- NOTE -->
Moving a button onto an image element 

.button-name{
    transform: translateY(-15px);
}

images can adhere to text-center and instead of img-fluid you can inline an exact height

<!-- NOTE -->
To unlink an a tag
.unlink{
    color: inherit;
    text-decoration: none;
}