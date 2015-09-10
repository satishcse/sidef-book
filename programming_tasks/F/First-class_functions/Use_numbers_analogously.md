[1]: http://rosettacode.org/wiki/First-class_functions/Use_numbers_analogously

# [First-class functions/Use numbers analogously][1]

```ruby
func multiplier(n1, n2) {
    closure { |n3|
        n1 * n2 * n3;
    }
}
 
var x  = 2.0;
var xi = 0.5;
var y  = 4.0;
var yi = 0.25;
var z  = (x + y);
var zi = (1 / (x + y));
 
var numbers = [x, y, z];
var inverses = [xi, yi, zi];
 
numbers.pair_with(inverses).each { |g, f|
    say multiplier(g, f)(0.5);
}
```

#### Output:
```
0.5
0.5
0.5
```