[1]: https://rosettacode.org/wiki/Last_letter-first_letter

# [Last letter-first letter][1]

```ruby
class LLFL(Array words) {
 
    has f = Hash()
 
    method init {
        words.each {|w|
            var m = w.match(/^(.).*(.)$/)
            f{m[0]}{w} = m[1]
        }
    }
 
    method longest_chain {
 
        var stack   = []
        var longest = []
 
        func poke(c) {
            var h = f{c}
 
            h.each_k { |word|
                var v = h.delete(word)
                stack.push(word)
                longest[] = stack[] if (stack.len > longest.len)
                __FUNC__(v) if f.exists(v)
                stack.pop
                h{word} = v
            }
        }
 
        f.each_k { poke(_) }
        return longest
    }
}
 
var words = %w(
  audino bagon baltoy banette bidoof braviary bronzor carracosta charmeleon
  cresselia croagunk darmanitan deino emboar emolga exeggcute gabite
  girafarig gulpin haxorus heatmor heatran ivysaur jellicent jumpluff kangaskhan
  kricketune landorus ledyba loudred lumineon lunatone machamp magnezone mamoswine
  nosepass petilil pidgeotto pikachu pinsir poliwrath poochyena porygon2
  porygonz registeel relicanth remoraid rufflet sableye scolipede scrafty seaking
  sealeo silcoon simisear snivy snorlax spoink starly tirtouga trapinch treecko
  tyrogue vigoroth vulpix wailord wartortle whismur wingull yamask
)
 
var obj = LLFL(words)
var longest = obj.longest_chain()
 
say "#{longest.len}: #{longest.join(' ')}"
```

#### Output:
```
23: machamp petilil landorus scrafty yamask kricketune exeggcute emboar registeel loudred darmanitan nosepass simisear rufflet trapinch heatmor relicanth haxorus seaking girafarig gabite emolga audino
```