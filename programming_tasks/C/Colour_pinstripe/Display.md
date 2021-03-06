[1]: https://rosettacode.org/wiki/Colour_pinstripe/Display

# [Colour pinstripe/Display][1]

```ruby
require('GD')
 
func pinstripes(width = 1280, height = 720) {
 
    var im = %O<GD::Image>.new(width, height)
    var colors = [0, 255].variations_with_repetition(3)
 
    var paintcolors = colors.shuffle.map {|rgb|
        im.colorAllocate(rgb...)
    }
 
    var starty     = 0
    var barheight  = height//4
 
    for barwidth in (1..4) {
        for (
            var(startx = 0, colorindex = 0);
            startx + barwidth <= width;
            startx += barwidth
        ) {
            im.filledRectangle(startx, starty, startx+barwidth,
                starty + barheight - 1, paintcolors[colorindex++ % 8])
        }
        starty += barheight
    }
 
    return im
}
 
File('pinstripes.png').write(pinstripes().png, :raw)
```