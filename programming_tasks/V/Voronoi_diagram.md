[1]: https://rosettacode.org/wiki/Voronoi_diagram

# [Voronoi diagram][1]

```ruby
require('Imager')

func generate_voronoi_diagram(width, height, num_cells) {
    var img = %O<Imager>.new(xsize => width, ysize => height)
    var (nx,ny,nr,ng,nb) = 5.of { [] }...

    for i in (^num_cells) {
        nx << rand(^width)
        ny << rand(^height)
        nr << rand(^256)
        ng << rand(^256)
        nb << rand(^256)
    }

    for y=(^height), x=(^width) {
        var j = (^num_cells -> min_by {|i| hypot(nx[i]-x, ny[i]-y) })
        img.setpixel(x => x, y => y, color => [nr[j], ng[j], nb[j]])
    }
    return img
}

var img = generate_voronoi_diagram(500, 500, 25)
img.write(file => 'VoronoiDiagram.png')
```

[Output image](https://github.com/trizen/rc/blob/master/img/voronoi-diagram-sidef.png)
