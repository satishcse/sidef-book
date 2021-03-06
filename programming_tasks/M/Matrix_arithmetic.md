[1]: https://rosettacode.org/wiki/Matrix_arithmetic

# [Matrix arithmetic][1]

The \`determinant\` method is provided by the Array class.

```ruby
class Array {
    method permanent {
        var r = @^self.len
 
        var sum = 0
        r.permutations { |*a|
            var prod = 1
            [a,r].zip {|row,col| prod *= self[row][col] }
            sum += prod
        }
 
        return sum
    }
}
 
var m1 = [[1,2],[3,4]]
 
var m2 = [[1, 2, 3, 4],
          [4, 5, 6, 7],
          [7, 8, 9, 10],
          [10, 11, 12, 13]]
 
var m3 = [[0, 1, 2, 3, 4],
          [5, 6, 7, 8, 9],
          [10, 11, 12, 13, 14],
          [15, 16, 17, 18, 19],
          [20, 21, 22, 23, 24]]
 
[m1, m2, m3].each { |m|
  say "determinant:\t #{m.determinant}\npermanent:\t #{m.permanent}\n"
}
```

#### Output:
```
determinant:     -2
permanent:       10

determinant:     0
permanent:       29556

determinant:     0
permanent:       6778800
```