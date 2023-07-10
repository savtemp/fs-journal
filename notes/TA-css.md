# CSS/SCSS/SASS

:root: using ‘:’ can be used to indicate variables we want to use throughout our style sheet 
Helpful when we don’t have a premade style sheet (SCSS)

:hover: gives you the ability to add hover properties to elements 
Select the style or element you want to select and then add the hover class → “.PROPERTY:hover”

Position Static: default value, all elements are in the order that they appear

Position Relative: the element is positioned relative to its normal position
Will have additional positioning attributes (top, bottom, left, right)
Element will be relative to itself - when the element moves, no other elements on the layout will be affected 

Position Absolute: the element is positioned absolutely to its first positioned parent
Allows you to place the element precisely where you want it 
Positioning is done relative to the first relatively OR absolutely positioned parent element 
If there is no positioned parent element then the element that has position absolute will be positioned directly related to the HTML element (the entire page)

Position Fixed: the element is positioned related to the browser window

Position Sticky: the element is positioned based on the user’s scroll position 
Sticky top generally used for navbar

@media rule: used in media queries to apply different styles for different media types/devices 
Can be used to check many things → width or height of viewport/device/orientation 
Popular technique for responsive web design 
Example providing the screen size for mobile 

@media (max-width 768 px){
	ADD STYLES HERE
}
