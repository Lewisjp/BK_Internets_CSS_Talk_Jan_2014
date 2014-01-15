**Jeremy**: Traditionally CSS has been for styling while content was reserved for HTML.  Today we have numerous tools that can blur these lines.  Loading image files can take time, and can appear differently based on monitor type.  By using CSS shapes instead of image files, data heavy web sites can lower load time, but depending on the user browder CSS shapes can be distorted.  

Today Hannah and I will review basic CSS shape building.  

###Question One: How we made the shapes

**Hannah**: I was responsible for the circle in our tic tac toe game.  The shape consists of a box with a green colored background and a border radius of 10%.  Positioned on top of this is a circle formed with a wide border and no background color.  To give the circle some dimension, I added a stacked box shadow to serve as a slight gradient between light and dark colors.  Lastly, positioned on top of this I positioned a smaller inner circle, which simply is a box shadow to give a corresponding feeling of dimension. 

**Jeremy**: Hannah’s Circle used border-radius of 50% to give curves to her O.  For the X shape I decided to use pointed corners, with the default border-radius of 0%.  

I gave the rectangles width of 18% of the parent element, the box.  When degrees are set to 0 the object is a straight line from top to bottom, with the height of the box.  I rotated the first rectangle 45 degrees.

For the second rectangle of the X, I could have rotated it 135 degrees, but instead used -45 so the relationship between the rectangles would be clearer to developers.  To maintain the proper direction of the shadows I had to switch the horizontal and vertical offsets of the shadow of the second line.  

The shadow effect of the two lines of the X, creates an outline around them.  This made it clear that the X consisted of two shapes.  To create the illusion of a solid X I added a 3rd rectangle, without a shadow, and overlaid it on top.  This top line was made slightly wider, to avoid seeing slight parts of the shadow that hinted the solid structure was an illusion.  

###Question Two: How we positioned them

**Hannah**: The body of the document is set to fixed at 100% of the desktop screen (no mention for viewport size on this.)  Each box is positioned relative to the body, and each circle is positioned relative to the parent element (the box).  The X’s are positioned absolutely to the parent element(the box).

**Jeremy**: In our HTML we placed the board in a division, div, container.  Within the container were three divs for the rows, that contained three box elements.  Each box gained a single shape, either X or O.  

###Question Three: What parts used a transition and what parts used a transform, and the differences between the two

**Hannah**: Neither of these boxes used transitions.  The circle used no transforms either.  The X’s used a transform property to rotate the rectangles to form the X.  Both the animated X and O boxes used Keyframes to animate them, which technically would probably fall under the “transitions” category in this case.

The difference between a CSS transition and a transform, in its simplest context, is this: A transition will smoothly change properties of an element over a specified amount of time whereas a transform will change elements on a 2D or 3D space. 

An example of a CSS transform would be text or body color changing upon hovering (or focusing) on an element.  An example of a CSS tranform is rotating an image on the screen on the X, Y or Z axis.

Its important to note that transitions and transforms do not physically change the position of the elements, they simply change the appearance of those elements on the browser. 

**Jeremy**: Our animation uses class selectors to determine the order of effects.  The animation uses Keyframes that begin with @-, for example @-webkit-keyframes followed by it's variable name.  For this example we'll use FadeInPlease.  This will join our keyframe and animation in our CSS.  This could allow for multiple separate animations.

The effect will start { from { opacity:0; } to { opacity:1; } }
Opacity determines how transparent our shape will be, with 0 being invisible and 1 as solid.   

Now we can apply our effect to selectors.  Once we choose the appropriate selectors we can add traits to our effect.

Animation-fill-mode determines what traits the image will keep once it ends.  Forwards will keep its final traits.  Backwards will set it to its original traits.  

Animation-duration determines how much time your animation will take in seconds.  

To create a series of events we can use more specific selectors to set animation-delay, in seconds, before an effect begins.


###Question Four: Browser support

**Hannah**: CSS transitions are supported in IE10 and above, Firefox 4.0 and above, Chrome 4.0 and above, Safari 3.1 and above, Opera 10.5 and above, iOS Safari 3.1 and above, Android browser 2.1 and above, Blackberry Browser 7.0 and above, Opera for Mobile 10.0 and above, and the current versions of Chrome, Firefox and IE for mobile devices.  CSS transforms are supported in IE9 and above, Firefox 3.5 and above, Chrome 4.0 and above, Safari 3.1 and above, Opera 10.5 and above, iOS Safari 3.2 and above, Android browser 2.1 and above, Blackberry Browser 7.0 and above, Opera for Mobile 11.0 and above, and the current versions of Chrome, Firefox and IE for mobile devices.

To ensure that you’ll have cross browser compatibility with your transitions and transforms, in your CSS element declaration, you should include the preferred standards for -webkit, -moz, -o and the default, in addition to 2-D equivalents for 3D transforms just in case you find one that is not supported by certain browsers.


