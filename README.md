# ext-op-ml. A class whith extension functions for use in Machine learning processes

## V.1.0.0

## You can to use in PHP functions as linspace, pow arrays, ....

Class that do some extended operations such math cacls, string calcs, gd calcs. Useful for calculations in graphs, Machine learning processes and others.

This package of methods has been created to bring together in a single package a set of tools used in machine learning processes.

 Python is a widely used language in Machine Learning, but there are few tools in PHP, so different useful tools have been created in this regard to bring Machine Learning closer to the PHP programming language.
 
 The linspace() method appears in almost all python examples, but in php we don't have any function, so now we have this function.
 
 Graphs in Pyplot are used to visualize the data. A library close to this use is being made in PHP. Some functions are required for this operation, such as going from inches to pixels or going from a hexadecimal color to its values in RGB.
 
 Knowing what a text occupies in pixels is very useful and is used in the graph generation functions, but since it is an element widely used for other utilities, it has also been decided to implement it in this library.
 
 Another of the functions widely used in graphing examples is the use of mathematical functions to square, cube, etc ... the values of an array. This function has been recursively created to be able to perform these calculations.
 
 In short, this set of methods aims to gather all those methods that are missing in Machine Learning processes in PHP, but which in turn, can be very useful for other types of applications.
 
 Why ext_op_ml name for this class???? First I wanted to specify it for mathematical functions, but since I needed other functions that were not related to calculations and to add others related to graphical topics, I decided to call it the Machine Learning operations extension: ext_op_ml, but as I have commented previously, its use is beyond the exclusive Machine Learning functions.
 
 
 # REQUERIMENTS:
 
 - A minimum (minimum, minimum, minimum requeriments is needed). Tested on:
 		
    - Simple Raspberry pi (B +	512MB	700 MHz ARM11) with Raspbian Lite PHP7.3 (i love this gadgets)  :heart_eyes:
 		
    - VirtualBox Ubuntu Server 20.04.2 LTS (Focal Fossa) with PHP7.4.3 
 
 
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
     
     Range of points, specified as a pair of numeric scalars. $start and $end define the interval over which linspace generates the points.
     
     $start and $end can be real or complex and $end can be greater or less than $start. If $end is less than $start, the vector contains descending values.
     
     If $numsamples is 1, linspace returns $ end.
     
     If $numsamples is zero or negative, linspace returns an empty 1-by-0 array.
     
     If $numsamples is not an integer value, linspace rounds down and returns floor ($numsamples) points.
 
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
 
 **Of course. You can use it freely :vulcan_salute::alien:**
 
 By Rafa.
 
 
 @author Rafael Martin Soto
 
 @author {@link http://www.inatica.com/ Inatica}
 
 @blog {@link https://rafamartin10.blogspot.com/ Rafael Martin's Blog}
 
 @since October 2021
 
 @version 1.0.0
 
 @license GNU General Public License v3.0
