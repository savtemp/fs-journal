# HTML

<!-- Command + / = opens comment -->

<!-- FIXME  -->
<!-- NOTE -->
<!-- REVIEW -->
<!-- SECTION -->

<!-- alt key can move a line of code  -->

Padding - the invisible space between content of a box and its border, pushes things in
- padding good for small changes, not good for arranging actual layout of page 

Border - outline or edge 

Margin - invisible space on the outside of the border - responsible to white space around boxes, pushes things away 

display flex/ display grid: .d-flex 
- is a utility CLASS
- works by changing the way it renders content
- displays content left to right 

flex content: helps with more responsive page layout 
- will be some kind of movable space 

pixel count is not responsive - it will change with the size of the screen 
- remedy make the picture itself a responsive size 

<!-- REVIEW re-ask -->
px vs em
- em based off of font size 
- px set amount 80px will always be 80px 

<!-- REVIEW check this topic again-->
Media Querie 

.pojects{
    flex-direction:row;
}

@media screen (max-width: 600px){
    .project{
        width: 100%;
    }
    .project{
        flex-direction: column;
    }
}
- stop applying these rules at 600px or bigger 
- min = stop applying these rules at 600px or smaller