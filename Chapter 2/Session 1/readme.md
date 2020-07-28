Calculation to only get the text to the left of the + separator in field "color"


          If(PatternCount ( Color ; "+" )=1; Left(Color; Position(Color;"+";1;1) -1); Color)
