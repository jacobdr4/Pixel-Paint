# Development

#4/20/20
1. Sucessfully imported the cinderblock CoC-Button

#4/23/20
1. Imported the cinderblock CoC-Core
2. Added the SetUpButtons() and SetCoordinates() methods for the buttons
3. Imports are unfortunately not working yet

#4/24/20
1. Changed the cinderblock to Cinder-UI after CoC-Button/CoC-Core were not working
2. Created four buttons that are displayed on the UI
3. Added CreateButton() Class that displays the buttons 

#4/26/20
1. Created the paintcanvas class with tool enums

#4/27/20
1. Added built in cinder methods for mouse control, including MouseDown(), MouseUp(), 
MouseMove(), and MouseDrag(). Also made instance variables to keep track of the location
of where the mouse was first pressed and the current location of the mouse.
2. Implemented the DrawLine() and DrawRect() methods that allows the user to draw
straight lines and rectangles, respectively. Used the cinder drawLine and drawStrokedRect
methods.
3. Implemented the DrawScribble() method so the user can freely draw on the screen. Used
the cinder shape2d class.
4. Added a Multislider UI element so the user can change the marker color
5. Changed the buttons to a radio so only one tool can be selected at a time. Still need
to implement the methods to change the tool based on the radio selection.
6. Changed the name of PaintCanvas to BoardUtils, since it better describes what the class
does
7. Created an Enum class of tools in boardutils.cpp, to easily select one

#4/28/20
1. Added OnButtonPress() method to my_app, which is called whenever a radio
button is pressed;
2. Deleted Board_Utils, moved enum class to my_app.h
3. Added Clear() method, which clears all drawings on the screen

#4/29/20
1. Created the Shape class, which represents a shape that the user has drawn on the 
screen. It allows the user to switch tools and draw multiple shapes on the screen
without anything being deleted.
2. Refactored code in my_app.cc to use the Shape class. 
   * Created a vector of shapes, in my_app.h to store all of the shapes
   * Deleted old methods that simply drew one shape on the screen at a time
   * Added shape to the vector whenever mouseDown() is called
   * Added shape.Update() to mouseDrag() to update the current shape that is
   being drawn
   * Used a for-each loop to continuously display every shape while drawing
   in mouseDrag()
3. Now, every tool works except Fill.

#4/30/20
1. Fill tool now works
2. Added SetBackgroundColor() method and background_color instance variable, 
which changes/stores the color of the background when the fill tool is selected

---
#5/1/20
1. Added unit testing for the Shape class
2. Added two new methods in Shape for testing purposes. GetShapeCoordinates()
and UpdateWithoutClearing().
3. Wrote method documentation in shape.h

#5/2/20
1. Implemented the sqlite-modern-cpp and sqlite3
libraries
2. Added save and load buttons to UI, added save and load tools to
the tool enum
3. Created the sqlite database where each shape will be saved to

#5/3/20
1. Initially got the save and loading functionality working using SQLlite.
Although it worked as intended for saving rectangles and lines, I realized
it would require another library in order to save scribbles. I decided to not
use SQL, and just use local variables that would hold saves as long as
the user kept on running the project.
2. Created two new instance variables, vector<Shape> saved_shapes
and Color saved_background. Refactored save and load to use these two variables
to store shapes and the background color.
3. Added an Ellipse button to the UI, allowing the user to draw ellipses. 
Refactored the shape class to draw ellipses and added the "Ellipse" enum to 
tools.

#5/4/20
1. Added an undo button that deletes the last shape that was drawn. Functionality
int the method Undo()
2. Added bounds detection through a variable, can_draw, and the method
MouseInBounds(). This is to prevent the mouse from drawing anything when
it is in the UI area. It was necessary to do this for the undo button to work.
3. Created the GetShapeTypeFromTool() method, which returns an enum
ShapeType based the the tool that is selected. Used this to delete repetitive
code in mouseDown().
4. Deleted the Clear() method since it was redundant, I only needed to call
shapes.clear().
5. Deleted the SQLite 3 and SQLite modern cpp libraries

#5/6/20
1. Finalized some formatting to complete the project
