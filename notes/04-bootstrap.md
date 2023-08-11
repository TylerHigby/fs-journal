# Bootstrap
Bootstrap is a framework for css
style sheet must come AFTER bootstrap
href bootstrap
href style.css
Bootstrap must contain row

You need a container to start with a bootstrap grid
class = container or container fluid

EXAMPLE
<body>
  <header class = "container-fluid">
    <section class = "row bg-black">
      <div class = "col-4 p-2 fw-bold fs-4">
    <section class ="row">
    <section class ="row">

row = makes row (rows are automatically display:flex)
bg- X = background color
col- (1-12) =column scaled size (can use with images)
col-md-6 (on screens larger than medium,col will be 6)
p- X  is padding
pe- X is padding end
ps- x is padding start
py- padding up/down
px- padding left/right
img-fluid fits image to whatever container it's in
w-50 sets width to 50%
text-center Centers text (Can use with images)
text- X sets text color
text-start aligns text to the left instead of centered
order- (0-5)  orders the elements of the column


Figma
skeleton outline first (header, main, footer)
class = "container fluid" in each of the header/main/footer
sections with class="row" within each header, main, footer
divs within sections with class="col-(1-12)"
style debug and add the class to the body
add notes to help visualize organization

set p tags margin to 0 in style because they have a margin by default


:root in style.css creates a variable to access
EXAMPLE
:root{
  --green: #11d200
}

.bg-green{
  background-color: var(--green)
}

position absolute must have a relative position to go off of. It will default to the webpage which is by default a relative position. instead, link the position absolute to the intended container.

@media(min-width:768px){
  background-image:url();
}