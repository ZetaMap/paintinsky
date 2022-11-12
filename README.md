# Paintinsky for Numworks and PC
This library add lot of draw methods for kandinsky library.

**Note:** if you read the code you risk not understanding anything, it's normal the library has been designed to be as optimized and small as possible, hence this somewhat strange syntax.


### Usable content
#### Public methods

**get_hpixel**:
* Parameters: ``x``, ``y``
* Description: Get pixel at (x, y) in hex format

**draw_circle():**
* Parameters: ``x``, ``y``, ``radius``, ``color``, ``back`` **[default: None]**, ``spader`` **[default: 1]**, ``semi`` **[default: False]**, ``reverse`` **[default: False]**
* Description: Draw circle at (x, y). ``back`` is backgroung color, None is transparent. ``spader`` is the spader of circle line. ``semi`` for a semi circle. ``reverse`` to reverse ``color`` and ``back`` color
* Example *(if reverse=True)*: If I call draw_circle(10,10,20,"red",reverse=True) the circle line will transparent and rest of rect is red.

**draw_circle():**
* Parameters: ``x``, ``y``, ``radius``, ``color``, ``back`` **[default: None]**, ``semi`` **[default: False]**, ``reverse`` **[default: False]**
* Description: Same as draw_circle() but is filled

**draw_rect():**
* Parameters: ``x``, ``y``, ``w``, ``h``, ``color``, ``spader`` **[default: 1]**
* Description: Draw just a rectangle at (x, y). ``spader`` is the spader of rectangle line

**draw_line():**
* Parameters: ``x1``, ``y1``, ``x2``, ``y2``, ``color``, ``spader`` **[default: 1]**
* Description: Draw a line at (x1, y1) to (x2, y2)

**get_screen():**
* Parameters: ``x``, ``y``, ``w``, ``h``, ``compress`` **[default: False]**
* Description: Get all pixels of part of screen at (x, y) to (w, h). ``compress`` to compress pixels array to string hex hash.
* Note: By default this method return an array of array of pixel, and if the selection if big, script can raise an OutOfMemoryError because it take lot of RAM. So is better to use ``compress`` to compress all at pixel hex hash

**parse_screen():**
* Parameters: ``x``, ``y``, ``hash`` , ``zoom`` **[default: 1]**
* Description: Parse pixels hash or array at (x, y). ``zoom`` to enlarge pixels
* Note: The method auto detect if is compressed pixel hex hash by using type, since is an str. For ``zoom`` parameter is by default at 1 because 1 pixel, so if you increase thee value (e.g. zoom=4) 1 compressed pixel take 4 pixel in screen at uncompress

**draw_text():**
* Parameters: ``text``, ``x``, ``y``, ``size`` **[default: 1]**, ``color`` **[default: (0,0,0)]**, ``bg`` **[default: (248,252,248)]**, ``hideModel`` **[default: True]**
* Description: Draw a sized text at (x, y). ``color`` is the text color, None value is transparent color. ``bg`` is the background color, None value is transparent color. ``hideModel`` to hide first text used to copy content and increase size (more info in Note).
* Note: in kandinsky is not possible to choose the size of font, so one way is drawing first text with default size and copy content for increase size of text. So, the ``hide Model`` parameter copies and saves the old area which will be replaced by the first text, then re-replaced by the saved area. This allows you to enlarge the size of the text without having to hide the model afterwards. **The only problem with this method is that it takes a long time, so if you have a script that writes a lot of text, it's best to keep hideModel=False and hide the pattern manually**
 
#### Other methods
*Is only use for library methods, but you can use they if you want.*

**HEX():**
* Parameters: ``v``, ``l`` **[default: 2]**
* Description: Convert integer to a filled hex value. ``l`` max hex length

**INT():**
* Parameters: ``v``
* Description: Convert an filled or not hex value to integer.
* Note: String hex value must don't have '0x' a start, this will add automatically for conversion

### Note
gp, sp, fr and ds are just kandinsky's functions with a shortened name to take as little storage as possible. So there is no need to import kandinsky after this library, you can use these functions.
**WARNING:** Compress algorithm of method get_screen() is under in development so don't use it for moment. 

### Why for pc?
Because [this](https://github.com/ZetaMap/Kandinsky-Numworks) exist.
