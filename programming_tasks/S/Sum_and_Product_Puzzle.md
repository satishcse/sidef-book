[1]: http://rosettacode.org/wiki/Sum_and_Product_Puzzle

# [Sum and Product Puzzle][1]

```ruby
func grep_uniq(a, by) { a.group_by{ .(by) }.values.grep{.len == 1}.map{_[0]} }
func sums     (n)     { 2 .. n//2 -> map {|i| [i, n-i] } }
 
var pairs = {|i| ([i] ~X (i+1 .. 98))... }.map(2..97)

var p_uniq = Hash()
p_uniq{grep_uniq(pairs, :prod).map { .to_s }...} = ()
 
var s_pairs = pairs.grep {|p| sums(p.sum).all { !p_uniq.contains(.to_s) } }
var p_pairs = grep_uniq(s_pairs, :prod)
var f_pairs = grep_uniq(p_pairs, :sum)
 
f_pairs.each { |p| printf("X = %d, Y = %d\n", p...) }
```

#### Output:
```
X = 4, Y = 13
```
