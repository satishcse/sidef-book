[1]: http://rosettacode.org/wiki/Elementary_cellular_automaton/Infinite_length

# [Elementary cellular automaton/Infinite length][1]

```ruby
func evolve(rule, bin) {
    var offset = 0
    var (l='', r='')
    Inf.times {
        bin.sub!(/^((.)\g2*)/, {|_s1, s2| l = s2; offset -= s2.len; s2*2 })
        bin.sub!(/(.)\g1*$/, {|s1| r = s1; s1*2 })
        printf("%5d| %s%s\n", offset, ' ' * (40 + offset), bin.tr('01','.#'))
        bin = [l*3, 0.to(bin.len-3).map{|i| bin.substr(i, 3) }..., r*3 ].map { |t|
                1 & (rule >> t.bin)
        }.join
    }
}
 
evolve(90, "010")
```

#### Output:
```
   -1|                                        ..#..
   -2|                                       ..#.#..
   -3|                                      ..#...#..
   -4|                                     ..#.#.#.#..
   -5|                                    ..#.......#..
   -6|                                   ..#.#.....#.#..
   -7|                                  ..#...#...#...#..
   -8|                                 ..#.#.#.#.#.#.#.#..
   -9|                                ..#...............#..
  -10|                               ..#.#.............#.#..
  -11|                              ..#...#...........#...#..
  -12|                             ..#.#.#.#.........#.#.#.#..
  -13|                            ..#.......#.......#.......#..
  -14|                           ..#.#.....#.#.....#.#.....#.#..
  -15|                          ..#...#...#...#...#...#...#...#..
  -16|                         ..#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#..
  -17|                        ..#...............................#..
  -18|                       ..#.#.............................#.#..
  -19|                      ..#...#...........................#...#..
  -20|                     ..#.#.#.#.........................#.#.#.#..
   ⋮
```