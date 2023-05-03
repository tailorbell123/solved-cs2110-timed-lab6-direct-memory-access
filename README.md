Download Link: https://assignmentchef.com/product/solved-cs2110-timed-lab6-direct-memory-access
<br>
For this assignment, you will complete five functions to draw an animation with 60 frames on the GBA screen. The animation has been provided as an array of unsigned short in snoopframes.c. We have also provided for your reference snoopframes.bmp, which displays the array in snoopframes.c.

The animation contained in the array has been provided for your reference as (snoop-inputanimation.gif). After completing the functions correctly, the animation should display as snoop-outputexpected.gif.

<strong>Note: </strong>In the snoopframes array, frames 0 → 14 are not flipped at all, frames 15 → 29 are flipped horizontally only, frames 30 → 44 are flipped both ways, and frames 45 → 59 are flipped vertically only.

<h2><a name="_Toc5570"></a>3.1         Provided Files</h2>

Several files are provided for running the animation:

main.c : Calls your code to draw the animation. You don’t need to touch this.

gba.c : Library functions for GBA and Mode 3 gba.h : Header file for GBA and Mode 3, as well as function prototypes dma.h : Header file for DMA uint.h : Header file for integer typedefs font.c : A font array used to draw text

The animation frames in snoopframes.c are accompanied by the header file snoopframes.h.

<h2><a name="_Toc5571"></a>3.2         Running the Animation</h2>

Please use the provided Makefile to start the program with make emu.

Once the animation has begun, you can manipulate it with the following input: Button A (Z) : Play and pause the animation

Button L (A) : If paused, step one frame backward

Button R (S) : If paused, step one frame forward

<h2><a name="_Toc5572"></a>3.3         Completing the Animation (tl06.c)</h2>

You must implement the following five functions in tl06.c:

<ol>

 <li>getPointerToCurrentFrame</li>

 <li>drawSquareImage</li>

 <li>drawSquareImageFlippedHorizontal</li>

 <li>drawSquareImageFlippedVertical</li>

 <li>drawSquareImageFlippedBoth</li>

</ol>

<strong>Note: The only file you need to edit is </strong>tl06.c<strong>.</strong>

<h1><a name="_Toc5573"></a>4           Instructions</h1>

<h2><a name="_Toc5574"></a>4.1         Getting the Correct Animation Frame</h2>

The animation frames are consecutive to one another in the snoopframes array. Observe that each frame is 160 × 160 (i.e. 25<em>,</em>600) pixels, there are 60 frames in the animation, and snoopframes has 1<em>,</em>536<em>,</em>000 unsigned shorts: (160 × 160) × 60 = 1<em>,</em>536<em>,</em>000.

Open snoop-inputimage.bmp to see the image this array was created from.

The function getPointerToCurrentFrame takes as parameters: a pointer to the beginning of the frames array (frames), the dimension of each square frame (img dimension), and the current frame (count).

You must calculate and return a pointer to the beginning of the correct frame.

<h2><a name="_Toc5575"></a>4.2         Drawing the Images</h2>

Some of the frames in the animation have been flipped horizontally, vertically, or both ways. To properly draw the animation, you will need to implement four functions with Direct Memory Access (DMA).

<em>Note: </em>Calling the correct functions on the correct frames is taken care of for you in main.c, provided you’ve correctly implemented getPointerToCurrentFrame.

All four of these functions will draw the image starting at the top left corner of the screen. Each image has an img dimension which is the size of its width, the same as its height. Remember, <strong>you must use DMA!</strong>

For more details on implementation please read the comments provided in tl06.c.

<ol>

 <li>drawSquareImage(const u16 *image, int img dimension):</li>

 <li>drawSquareImageFlippedHorizontal(const u16 *image, int img dimension):</li>

 <li>drawSquareImageFlippedVertical(const u16 *image, int img dimension):</li>

 <li>drawSquareImageFlippedBoth(const u16 *image, int img dimension):</li>

</ol>

<h1><a name="_Toc5576"></a>5           Testing Your Work</h1>

To debug your work, run make emu in the directory and step through frame-by-frame to check how your functions are drawing to the screen.

Uploading tl06.c to the Gradescope assignment will check your assignment against our tests. You may resubmit your work as many times as needed, until you sign out and leave the classroom.