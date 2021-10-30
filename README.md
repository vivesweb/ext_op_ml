# ext-op-ml. A class whith extension functions for use in Machine Learning processes

## V.1.0.5

## Functions as linspace(), arrays pow() and others in PHP

Class that do some extended operations such math cacls, string calcs, gd calcs. Useful for calculations in graphs, Machine learning processes and others.

This package of methods has been created to bring together in a single package a set of tools used in machine learning processes.

 Python is a widely used language in Machine Learning, but there are few tools in PHP, so different useful tools have been created in this regard to bring Machine Learning closer to the PHP programming language.
 
 The numpy linspace() method appears in almost all pyplot python examples, but in php we don't have any function, so now we have this function.
 
 Graphs in Pyplot are used to visualize the data. A library close to this use is being made in PHP. Some functions are required for this operation, such as going from inches to pixels or going from a hexadecimal color to its values in RGB.
 
 Knowing what a text occupies in pixels is very useful and is used in the graph generation functions, but since it is an element widely used for other utilities, it has also been decided to implement it in this library.
 
 Another of the functions widely used in graphing examples is the use of mathematical functions to square, cube, etc ... the values of an array. This function has been recursively created to be able to perform these calculations.
 
 In short, this set of methods aims to gather all those methods that are missing in Machine Learning processes in PHP, but which in turn, can be very useful for other types of applications.
 
 Why ext_op_ml name for this class???? First I wanted to specify it for mathematical functions, but since I needed other functions that were not related to calculations and to add others related to graphical topics, I decided to call it the Machine Learning operations extension: ext_op_ml, but as I have commented previously, its use is beyond the exclusive Machine Learning functions.
 
 # AN EXAMPLE OF THE USE linspace() & pow() numpy PYPLOT IN PHP:
 
 	// NOTE: The graph library will be published soon. this example is only to see the use of Linspace() & pow()
	// We assume that $ax in PHP is a graph_object, and create an ext_op_ml object in $m variable
 
  	// PYTHON PYPLOT
 	
	x = np.linspace(0, 2, 100)
	
	ax.plot(x, x, label='linear')  # Plot some data on the axes.
	ax.plot(x, x**2, label='quadratic')  # Plot more data on the axes...
	ax.plot(x, x**3, label='cubic')  # ... and some more.
 
 	// PHP
 	$m = new ext_op_ml();
	
	$x = $m->linspace( 0, 2, 100 );
	
	$ax->plot( $x, $x, ['label'=>'linear'] );
	$ax->plot( $x, $m->pow($x, 2), ['label'=>'quadratic'] );
	$ax->plot( $x, $m->pow($x, 3), ['label'=>'cubic'] );
 
 
 # REQUERIMENTS:
 
 - A minimum (minimum, minimum, minimum requeriments is needed). Tested on:
 		
    - Simple Raspberry pi (B +	512MB	700 MHz ARM11) with Raspbian Lite PHP7.3 (i love this gadgets)  :heart_eyes:
 		
    - VirtualBox Ubuntu Server 20.04.2 LTS (Focal Fossa) with PHP7.4.3

    - If you use str_len_ttf() you need to sepecify the path file of your .ttf file. In this example we use DejaVuSnas.ttf file that you can download at https://dejavu-fonts.github.io/. It uses GD library, then your PHP system will need it: sudo apt install php-gd. Note: This function is only available if PHP is compiled with freetype support (--with-freetype-dir=DIR). See https://www.php.net/manual/en/function.imagettfbbox.php
 
 
  # FILES:
 There are 2 basic files:
 
 *ext-opl-ml.class.php* -> **Master class**. This file is the main file that you need to include in your code
 
 *example.class.php* -> **example for this class**
 
 
 # INSTALLATION:
 A lot of easy :smiley:. It is written in PURE PHP. Only need to include the files. Tested on basic PHP installation
 
          require_once __DIR__ . '/ext-op-ml-php.class.php';
 
# RESUME OF METHODS:

- **CREATE EXT OP ML:**
 
*new ext_op_ml(  );*

Example:

         $ext_op = new ext_op_ml();



- **linspace() CREATE INCREMENTAL ARRAY OF N ELEMENTS FROM X1 TO X2:**
 
Return an array with incremental values with steps. Space between points will be ($end-$start)/($numsamples-1)
     
- Range of points, specified as a pair of numeric scalars. $start and $end define the interval over which linspace generates the points.
     
- $start and $end can be real or complex and $end can be greater or less than $start. If $end is less than $start, the vector contains descending values.
     
- If $numsamples is 1, linspace returns $end.
     
- If $numsamples is zero or negative, linspace returns an empty 1-by-0 array.
     
- If $numsamples is not an integer value, linspace rounds down and returns floor ($numsamples) points.
 
*linspace( $start, $end, $numsamples = null )*

Example:

    $ext_op->linspace( -5, 5, 7 );
    
    return:  array(7) { [0]=> float(-5) [1]=> float(-3.3333333333333) [2]=> float(-1.6666666666667) [3]=> float(0) [4]=> float(1.6666666666667) [5]=> float(3.3333333333333) [6]=> float(5) }


- **pow() POW A VALUE OR AN ARRAY OF VALUES:**
 
*pow( $values, $exp = 2 )*

Example:

        $ext_op->pow( [2, 4, 6], 3 )
        
        return: array(3) { [0]=> int(8) [1]=> int(64) [2]=> int(216) }



- **GET THE SIZE IN PIXELS OF LENGTH OF STRING IN FONT & SIZE FORMAT GIVEN:**

  In font_path you need to sepecify where is the .ttf file

*str_len_ttf( $text, $font_path, $font_size, $angle = 0 )*

Example:

        $ext_op->str_len_ttf( "Hellow Wold", __DIR__ . "/fonts/dejavu-fonts-ttf-2.37/ttf/DejaVuSans.ttf", 12 )
        
        return: int(100)
	
	
- **TRANSFORM INCHES TO PIXELS:**

*inch_2_pixels( $size_inch, $dpis = 72 )*

Example (6.4 Inches at 100 dpis's in pixels):

        $ext_op->inch_2_pixels( 6.4, 100)
        
        return int(640)



- **TRANSFORM HEXADECIMAL COLOR TO RGB ARRAY:**

*hex2rgb( $hex_color )*

Example (6.4 Inches at 100 dpis's in pixels):

        $ext_op->hex2rgb( "#1f77b4" )
        
        return array(3) { [0]=> int(31) [1]=> int(119) [2]=> int(180) }
	
**OUTPUT OF THE example.php FILE**

		linspace( -5, 5 ): -5 to 5 array in 100 steps:
		array(100) { [0]=> float(-5) [1]=> float(-4.8989898989899) [2]=> float(-4.7979797979798) [3]=> float(-4.6969696969697) [4]=> float(-4.5959595959596) [5]=> float(-4.4949494949495) [6]=> float(-4.3939393939394) [7]=> float(-4.2929292929293) [8]=> float(-4.1919191919192) [9]=> float(-4.0909090909091) [10]=> float(-3.989898989899) [11]=> float(-3.8888888888889) [12]=> float(-3.7878787878788) [13]=> float(-3.6868686868687) [14]=> float(-3.5858585858586) [15]=> float(-3.4848484848485) [16]=> float(-3.3838383838384) [17]=> float(-3.2828282828283) [18]=> float(-3.1818181818182) [19]=> float(-3.0808080808081) [20]=> float(-2.979797979798) [21]=> float(-2.8787878787879) [22]=> float(-2.7777777777778) [23]=> float(-2.6767676767677) [24]=> float(-2.5757575757576) [25]=> float(-2.4747474747475) [26]=> float(-2.3737373737374) [27]=> float(-2.2727272727273) [28]=> float(-2.1717171717172) [29]=> float(-2.0707070707071) [30]=> float(-1.969696969697) [31]=> float(-1.8686868686869) [32]=> float(-1.7676767676768) [33]=> float(-1.6666666666667) [34]=> float(-1.5656565656566) [35]=> float(-1.4646464646465) [36]=> float(-1.3636363636364) [37]=> float(-1.2626262626263) [38]=> float(-1.1616161616162) [39]=> float(-1.0606060606061) [40]=> float(-0.95959595959596) [41]=> float(-0.85858585858586) [42]=> float(-0.75757575757576) [43]=> float(-0.65656565656566) [44]=> float(-0.55555555555556) [45]=> float(-0.45454545454546) [46]=> float(-0.35353535353535) [47]=> float(-0.25252525252525) [48]=> float(-0.15151515151515) [49]=> float(-0.05050505050505) [50]=> float(0.05050505050505) [51]=> float(0.15151515151515) [52]=> float(0.25252525252525) [53]=> float(0.35353535353535) [54]=> float(0.45454545454545) [55]=> float(0.55555555555556) [56]=> float(0.65656565656566) [57]=> float(0.75757575757576) [58]=> float(0.85858585858586) [59]=> float(0.95959595959596) [60]=> float(1.0606060606061) [61]=> float(1.1616161616162) [62]=> float(1.2626262626263) [63]=> float(1.3636363636364) [64]=> float(1.4646464646465) [65]=> float(1.5656565656566) [66]=> float(1.6666666666667) [67]=> float(1.7676767676768) [68]=> float(1.8686868686869) [69]=> float(1.969696969697) [70]=> float(2.0707070707071) [71]=> float(2.1717171717172) [72]=> float(2.2727272727273) [73]=> float(2.3737373737374) [74]=> float(2.4747474747475) [75]=> float(2.5757575757576) [76]=> float(2.6767676767677) [77]=> float(2.7777777777778) [78]=> float(2.8787878787879) [79]=> float(2.979797979798) [80]=> float(3.0808080808081) [81]=> float(3.1818181818182) [82]=> float(3.2828282828283) [83]=> float(3.3838383838384) [84]=> float(3.4848484848485) [85]=> float(3.5858585858586) [86]=> float(3.6868686868687) [87]=> float(3.7878787878788) [88]=> float(3.8888888888889) [89]=> float(3.989898989899) [90]=> float(4.0909090909091) [91]=> float(4.1919191919192) [92]=> float(4.2929292929293) [93]=> float(4.3939393939394) [94]=> float(4.4949494949495) [95]=> float(4.5959595959596) [96]=> float(4.6969696969697) [97]=> float(4.7979797979798) [98]=> float(4.8989898989899) [99]=> float(5) }

		linspace( -5, 5, 7 ): -5 to 5 array in 7 steps:
		array(7) { [0]=> float(-5) [1]=> float(-3.3333333333333) [2]=> float(-1.6666666666667) [3]=> float(0) [4]=> float(1.6666666666667) [5]=> float(3.3333333333333) [6]=> float(5) }

		pow( [2, 4, 6] ): Pow 2 array [2, 4, 6]:
		array(3) { [0]=> int(4) [1]=> int(16) [2]=> int(36) }

		pow( [2, 4, 6], 3 ): Pow 3 array [2, 4, 6]:
		array(3) { [0]=> int(8) [1]=> int(64) [2]=> int(216) }

		str_len_ttf( "Hellow Wold", __DIR__ . "/fonts/dejavu-fonts-ttf-2.37/ttf/DejaVuSans.ttf", 12 ): Length in pixels of "Hellow Wold" string, with DejaVuSans & size 12:
		int(100)

		inch_2_pixels( 6.4, 100): 6.4 inches at 100 dpis in Pixels:
		int(640)

		hex2rgb( "#1f77b4" ): Color "#1f77b4" in vector of integers RGB:
		array(3) { [0]=> int(31) [1]=> int(119) [2]=> int(180) }
 
 **FROM V.1.0.1**

- **Added copysign()**

 Returns the magnitude value with the sign of the sign number. Thanks to https://github.com/markrogoyski/math-php/blob/master/src/Arithmetic.php

*copySign(float $magnitude, float $sign)*

Example:

        $sign = $ext_op->copysign(1, -50);
        
        return float(-1)
	
 **FROM V.1.0.2**

- **Added avg()**

 Returns the average in array

*avg($array)*

Example:

        avg([1, 2, 3, 4, 5])
        return int(3)
	

- **Added binarySearch()**

 Returns the id in array of searched value. If not found it returns false. NOTE: Be carefull with comparations on id = 0 and id = false. Use: if( binarySearch() === false )

*binarySearch($arr, $x)*

Example:

        binarySearch([1, 2, 3, 4, 5], 4)
        return int(3)
	

- **Added freq()**

 Returns the requency defined in range in array of values.
 
 If your array is sorted, you can specify it to do a fastest search
 
 You can define if the $max value is included in the range or not

*freq($arrval, $min, $max, $includemax = false, $arrvalsorted = false)*

Example:

        freq([1, 2, 2, 3, 3, 4, 5], 2, 3)
        return int(2)

        freq([1, 2, 2, 3, 3, 4, 5], 2, 3, true)
        return int(4)
	
**FROM V.1.0.3**

- **Added arr_max_len_ttf()**

 Returns the max length in pixels of .ttf array strings

*arr_max_len_ttf( $arr, $font_path, $font_size, $angle = 0 )*

Example:

        $font_path  = __DIR__ . '/DejaVuSans.ttf';
        $font_size  = 10;
	$arr = [ 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'];
        $max_length = $this->arr_max_len_ttf( $arr, $font_path, $font_size ); // Return the size in pixels of 'Wednesday', that is the longest string in the array
	
**FROM V.1.0.4**


- **GET THE SIZE IN PIXELS OF HEIGHT OF STRING IN FONT & SIZE FORMAT GIVEN:**

  In font_path you need to sepecify where is the .ttf file

*str_height_ttf( $text, $font_path, $font_size, $angle = 0 )*

Example:

        $ext_op->str_height_ttf( "Hellow Wold", __DIR__ . "/fonts/dejavu-fonts-ttf-2.37/ttf/DejaVuSans.ttf", 12 )


- **GET IF ARRAY IS ASSOCIATIVE ARRAY:**

*is_assoc( $arr )*

Example:

        $ext_op->is_assoc( [10, 20, 30] ) // Return false
	$ext_op->is_assoc( ['Morning' = 10, 'Afternoon' => 20, 'Night' => 30] ) // Return true
        **FROM V.1.0.4**

**FROM V.1.0.5**

- **GET ARRAY OF ID_COL OF DATASET:**

  Return an array of one col of dataset given by id_col. You can skip rows (for example when first row is the name of the cols)

*arrdatasetcol($dataset, $col_id, $skipnrows = 0)*

Example:

        $arrdatasetcol = $ext_op->arrdatasetcol( $dataset, 1 ); // Dataset is array of csv, for example, And 1 is for skip first row if is col names
 
 **Of course. You can use it freely :vulcan_salute::alien:**
 
 By Rafa.
 
 
 @author Rafael Martin Soto
 
 @author {@link http://www.inatica.com/ Inatica}
 
 @blog {@link https://rafamartin10.blogspot.com/ Rafael Martin's Blog}
 
 @since October 2021
 
 @version 1.0.5
 
 @license GNU General Public License v3.0
