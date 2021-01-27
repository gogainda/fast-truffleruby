## Fast Truffle Ruby 


The idia of this project is to run all collected examples from the [Fast Ruby] (https://github.com/JuanitoFatas/fast-ruby) and run it against the latest truffle ruby version to see if the same results hold for the Truffle ruby. 

As you will see in the resalst below some results a quite different
1773.87s user 39.75s system 141% cpu 21:18.57 total
## Results
```
$ ruby -v code/general/array-argument-vs-splat-arguments.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       304.624M i/100ms
Function with splat arguments
                         1.461k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          3.100B (± 0.5%) i/s -     15.536B in   5.011489s
Function with splat arguments
                         14.648k (± 1.7%) i/s -     74.511k in   5.088046s

Comparison:
Function with single Array argument: 3100123270.1 i/s
Function with splat arguments:    14648.5 i/s - 211634.43x  (± 0.00) slower

$ ruby -v code/general/assignment.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   310.773M i/100ms
Sequential Assignment
                       310.952M i/100ms
Calculating -------------------------------------
 Parallel Assignment      3.091B (± 0.9%) i/s -     15.539B in   5.027062s
Sequential Assignment
                          3.098B (± 0.7%) i/s -     15.548B in   5.019528s

Comparison:
Sequential Assignment: 3097589521.8 i/s
 Parallel Assignment: 3091254558.9 i/s - same-ish: difference falls within error

$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   294.506M i/100ms
       attr_accessor   294.741M i/100ms
Calculating -------------------------------------
   getter_and_setter      2.919B (± 1.7%) i/s -     14.725B in   5.046529s
       attr_accessor      2.742B (± 1.4%) i/s -     13.853B in   5.053577s

Comparison:
   getter_and_setter: 2918800024.6 i/s
       attr_accessor: 2741726297.2 i/s - 1.06x  (± 0.00) slower

$ ruby -v code/general/begin-rescue-vs-respond-to.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     8.956k i/100ms
         respond_to?   270.902M i/100ms
Calculating -------------------------------------
      begin...rescue     69.596k (± 0.6%) i/s -    349.284k in   5.018928s
         respond_to?      2.809B (± 2.2%) i/s -     14.087B in   5.017884s

Comparison:
         respond_to?: 2808762372.0 i/s
      begin...rescue:    69595.8 i/s - 40358.21x  (± 0.00) slower

$ ruby -v code/general/block-apply-method.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   286.580M i/100ms
             &method   286.808M i/100ms
Calculating -------------------------------------
              normal      2.921B (± 1.9%) i/s -     14.616B in   5.005512s
             &method      3.059B (± 1.6%) i/s -     15.488B in   5.064029s

Comparison:
             &method: 3059170083.5 i/s
              normal: 2920979505.7 i/s - 1.05x  (± 0.00) slower

$ ruby -v code/general/define_method-vs-module-eval.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                        74.000  i/100ms
       define_method   396.000  i/100ms
Calculating -------------------------------------
module_eval with string
                        492.574  (±36.3%) i/s -      2.072k in   5.108132s
       define_method      2.428k (±33.4%) i/s -     10.692k in   5.796540s

Comparison:
       define_method:     2427.6 i/s
module_eval with string:      492.6 i/s - 4.93x  (± 0.00) slower

$ ruby -v code/general/format-vs-round-and-to-s.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    52.092k i/100ms
       Kernel#format    70.843k i/100ms
            String#%    69.839k i/100ms
Calculating -------------------------------------
         Float#round    523.791k (± 1.0%) i/s -      2.657M in   5.072553s
       Kernel#format    713.675k (± 1.5%) i/s -      3.613M in   5.063692s
            String#%    728.295k (± 5.4%) i/s -      3.632M in   5.008800s

Comparison:
            String#%:   728294.8 i/s
       Kernel#format:   713674.7 i/s - same-ish: difference falls within error
         Float#round:   523791.0 i/s - 1.39x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct-on-access.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   302.533M i/100ms
          OpenStruct    63.047M i/100ms
Calculating -------------------------------------
                Hash      3.025B (± 0.2%) i/s -     15.127B in   5.000095s
          OpenStruct    630.566M (± 0.1%) i/s -      3.215B in   5.099219s

Comparison:
                Hash: 3025284429.5 i/s
          OpenStruct: 630566275.0 i/s - 4.80x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   300.364M i/100ms
          OpenStruct   302.670M i/100ms
Calculating -------------------------------------
                Hash      3.022B (± 0.6%) i/s -     15.319B in   5.068599s
          OpenStruct      3.062B (± 1.3%) i/s -     15.436B in   5.042819s

Comparison:
          OpenStruct: 3061502425.0 i/s
                Hash: 3022379463.2 i/s - same-ish: difference falls within error

$ ruby -v code/general/inheritance-check.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal     1.113M i/100ms
  ancestors.include?   167.948k i/100ms
Calculating -------------------------------------
  less than or equal     11.052M (± 1.4%) i/s -     55.667M in   5.037559s
  ancestors.include?      1.633M (± 0.5%) i/s -      8.229M in   5.038949s

Comparison:
  less than or equal: 11052451.9 i/s
  ancestors.include?:  1633208.8 i/s - 6.77x  (± 0.00) slower

$ ruby -v code/general/loop-vs-while-true.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     1.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     28.667  (± 0.0%) i/s -    144.000  in   5.023200s
         Kernel loop      7.405  (± 0.0%) i/s -     37.000  in   5.005731s

Comparison:
          While Loop:       28.7 i/s
         Kernel loop:        7.4 i/s - 3.87x  (± 0.00) slower

$ ruby -v code/array/array-first-vs-index.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   184.072M i/100ms
         Array#first   184.137M i/100ms
Calculating -------------------------------------
           Array#[0]      1.841B (± 0.2%) i/s -      9.388B in   5.098400s
         Array#first      1.854B (± 1.2%) i/s -      9.391B in   5.067040s

Comparison:
         Array#first: 1853601839.2 i/s
           Array#[0]: 1841301748.6 i/s - same-ish: difference falls within error

$ ruby -v code/array/array-last-vs-index.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   297.267M i/100ms
          Array#last   302.903M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.026B (± 0.2%) i/s -     15.161B in   5.010197s
          Array#last      3.035B (± 0.8%) i/s -     15.448B in   5.090589s

Comparison:
          Array#last: 3034824463.3 i/s
          Array#[-1]: 3025956860.7 i/s - same-ish: difference falls within error

$ ruby -v code/array/bsearch-vs-find.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   395.856k i/100ms
Calculating -------------------------------------
                find      0.105  (± 0.0%) i/s -      1.000  in   9.511739s
             bsearch      4.023M (±14.7%) i/s -     19.793M in   5.038306s

Comparison:
             bsearch:  4023015.0 i/s
                find:        0.1 i/s - 38265867.44x  (± 0.00) slower

$ ruby -v code/array/insert-vs-unshift.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.150  (± 0.0%) i/s -      1.000  in   6.658115s
        Array#insert      0.280  (± 0.0%) i/s -      2.000  in   7.152817s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.86x  (± 0.00) slower

$ ruby -v code/array/length-vs-size-vs-count.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   286.936M i/100ms
          Array#size   286.763M i/100ms
         Array#count   286.739M i/100ms
Calculating -------------------------------------
        Array#length      2.911B (± 1.4%) i/s -     14.634B in   5.028645s
          Array#size      3.017B (± 1.0%) i/s -     15.198B in   5.037795s
         Array#count      3.086B (± 1.1%) i/s -     15.484B in   5.018515s

Comparison:
         Array#count: 3085745103.6 i/s
          Array#size: 3017211941.6 i/s - 1.02x  (± 0.00) slower
        Array#length: 2910615214.7 i/s - 1.06x  (± 0.00) slower

$ ruby -v code/array/shuffle-first-vs-sample.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    33.006k i/100ms
        Array#sample     3.524M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    322.146k (± 6.3%) i/s -      1.617M in   5.055084s
        Array#sample     35.275M (± 1.4%) i/s -    179.710M in   5.095640s

Comparison:
        Array#sample: 35274859.2 i/s
 Array#shuffle.first:   322146.4 i/s - 109.50x  (± 0.00) slower

$ ruby -v code/date/iso8601-vs-parse.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601   580.000  i/100ms
          Date.parse     2.547k i/100ms
Calculating -------------------------------------
        Date.iso8601     31.641k (± 9.9%) i/s -    156.600k in   5.001393s
          Date.parse     36.053k (± 1.7%) i/s -    180.837k in   5.017270s

Comparison:
          Date.parse:    36052.9 i/s
        Date.iso8601:    31641.1 i/s - 1.14x  (± 0.00) slower

$ ruby -v code/enumerable/each-push-vs-map.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   249.309k i/100ms
           Array#map   667.351k i/100ms
Calculating -------------------------------------
   Array#each + push      2.695M (± 2.3%) i/s -     13.463M in   4.998622s
           Array#map      7.518M (± 2.2%) i/s -     38.039M in   5.062217s

Comparison:
           Array#map:  7517989.0 i/s
   Array#each + push:  2694698.3 i/s - 2.79x  (± 0.00) slower

$ ruby -v code/enumerable/each-vs-for-loop.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop     1.045M i/100ms
               #each     1.030M i/100ms
Calculating -------------------------------------
            For loop     10.554M (± 1.3%) i/s -     53.293M in   5.050303s
               #each     10.982M (± 1.4%) i/s -     55.611M in   5.064993s

Comparison:
               #each: 10981700.8 i/s
            For loop: 10554208.6 i/s - 1.04x  (± 0.00) slower

$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   457.284k i/100ms
     each_with_index   843.683k i/100ms
Calculating -------------------------------------
          While Loop      4.581M (± 0.3%) i/s -     23.321M in   5.091393s
     each_with_index      8.724M (± 0.5%) i/s -     43.872M in   5.028703s

Comparison:
     each_with_index:  8724473.3 i/s
          While Loop:  4580601.8 i/s - 1.90x  (± 0.00) slower

$ ruby -v code/enumerable/inject-symbol-vs-block.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   185.362k i/100ms
      inject to_proc   185.373k i/100ms
        inject block   185.302k i/100ms
Calculating -------------------------------------
       inject symbol      1.853M (± 0.2%) i/s -      9.268M in   5.000742s
      inject to_proc      1.851M (± 0.4%) i/s -      9.269M in   5.006371s
        inject block      1.876M (± 1.5%) i/s -      9.450M in   5.039667s

Comparison:
        inject block:  1875629.3 i/s
       inject symbol:  1853349.3 i/s - same-ish: difference falls within error
      inject to_proc:  1851407.3 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    22.091k i/100ms
   Array#map.flatten    21.461k i/100ms
      Array#flat_map    54.641k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    214.860k (± 0.9%) i/s -      1.082M in   5.038425s
   Array#map.flatten    209.050k (± 0.8%) i/s -      1.052M in   5.030671s
      Array#flat_map    531.505k (± 0.5%) i/s -      2.677M in   5.037524s

Comparison:
      Array#flat_map:   531504.8 i/s
Array#map.flatten(1):   214859.7 i/s - 2.47x  (± 0.00) slower
   Array#map.flatten:   209049.8 i/s - 2.54x  (± 0.00) slower

$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   211.964k i/100ms
  Array#reverse_each   480.269k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.125M (± 0.9%) i/s -     10.810M in   5.086554s
  Array#reverse_each      4.802M (± 0.1%) i/s -     24.013M in   5.000224s

Comparison:
  Array#reverse_each:  4802478.2 i/s
  Array#reverse.each:  2125397.8 i/s - 2.26x  (± 0.00) slower

$ ruby -v code/enumerable/select-first-vs-detect.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       606.484k i/100ms
   Enumerable#detect     3.621M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          6.340M (± 2.8%) i/s -    126.755M in  20.010523s
   Enumerable#detect     39.183M (± 0.5%) i/s -    785.656M in  20.051378s

Comparison:
   Enumerable#detect: 39183132.1 i/s
Enumerable#select.first:  6339624.4 i/s - 6.18x  (± 0.00) slower

$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       217.075k i/100ms
Enumerable#select.last
                       342.406k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.159M (± 1.5%) i/s -     10.854M in   5.028519s
Enumerable#select.last
                          3.417M (± 1.0%) i/s -     17.120M in   5.010830s

Comparison:
Enumerable#select.last:  3417038.3 i/s
Enumerable#reverse.detect:  2158967.9 i/s - 1.58x  (± 0.00) slower

$ ruby -v code/enumerable/sort-vs-sort_by.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         4.025k i/100ms
  Enumerable#sort_by     4.189k i/100ms
     Enumerable#sort     5.248k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         38.726k (±12.2%) i/s -    185.150k in   5.080287s
  Enumerable#sort_by     38.526k (±13.2%) i/s -    180.127k in   5.063910s
     Enumerable#sort     58.651k (± 1.7%) i/s -    293.888k in   5.012335s

Comparison:
     Enumerable#sort:    58651.1 i/s
Enumerable#sort_by (Symbol#to_proc):    38726.0 i/s - 1.51x  (± 0.00) slower
  Enumerable#sort_by:    38525.6 i/s - 1.52x  (± 0.00) slower

$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   266.092k i/100ms
Enumerable#sort_by...first
                         8.637k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      2.680M (± 1.3%) i/s -     13.571M in   5.064515s
Enumerable#sort_by...first
                         89.716k (± 1.4%) i/s -    449.124k in   5.007034s

Comparison:
   Enumerable#min_by:  2679982.7 i/s
Enumerable#sort_by...first:    89716.4 i/s - 29.87x  (± 0.00) slower

$ ruby -v code/hash/bracket-vs-dup.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   595.394k i/100ms
            Hash#dup   593.106k i/100ms
Calculating -------------------------------------
              Hash[]      5.902M (± 1.2%) i/s -     29.770M in   5.044591s
            Hash#dup      5.955M (± 1.1%) i/s -     30.248M in   5.080462s

Comparison:
            Hash#dup:  5954622.6 i/s
              Hash[]:  5902184.6 i/s - same-ish: difference falls within error

$ ruby -v code/hash/bracket-vs-fetch.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   286.732M i/100ms
  Hash#fetch, symbol   179.242M i/100ms
     Hash#[], string     8.747M i/100ms
  Hash#fetch, string     7.650M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      2.872B (± 0.7%) i/s -     14.623B in   5.091924s
  Hash#fetch, symbol      1.890B (± 1.9%) i/s -      9.500B in   5.027163s
     Hash#[], string     94.290M (± 0.9%) i/s -    472.356M in   5.010012s
  Hash#fetch, string     82.549M (± 1.1%) i/s -    413.123M in   5.005259s

Comparison:
     Hash#[], symbol: 2871990597.1 i/s
  Hash#fetch, symbol: 1890372093.9 i/s - 1.52x  (± 0.00) slower
     Hash#[], string: 94289527.5 i/s - 30.46x  (± 0.00) slower
  Hash#fetch, string: 82548599.4 i/s - 34.79x  (± 0.00) slower

$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig   821.810k i/100ms
             Hash#[]     5.112M i/100ms
          Hash#[] ||     5.112M i/100ms
          Hash#[] &&     5.113M i/100ms
          Hash#fetch     4.911M i/100ms
 Hash#fetch fallback     4.918M i/100ms
Calculating -------------------------------------
            Hash#dig      8.306M (± 0.9%) i/s -     41.912M in   5.046221s
             Hash#[]     51.126M (± 0.1%) i/s -    255.613M in   4.999647s
          Hash#[] ||     51.126M (± 0.1%) i/s -    260.714M in   5.099414s
          Hash#[] &&     51.065M (± 0.5%) i/s -    255.638M in   5.006254s
          Hash#fetch     49.501M (± 1.2%) i/s -    250.449M in   5.060118s
 Hash#fetch fallback     50.385M (± 0.2%) i/s -    255.744M in   5.075798s

Comparison:
          Hash#[] ||: 51126369.2 i/s
             Hash#[]: 51126339.9 i/s - same-ish: difference falls within error
          Hash#[] &&: 51064990.5 i/s - same-ish: difference falls within error
 Hash#fetch fallback: 50385110.3 i/s - 1.01x  (± 0.00) slower
          Hash#fetch: 49501289.9 i/s - 1.03x  (± 0.00) slower
            Hash#dig:  8306374.4 i/s - 6.16x  (± 0.00) slower

$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   310.793M i/100ms
  Hash#fetch + block   309.992M i/100ms
    Hash#fetch + arg   308.869M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      3.100B (± 0.6%) i/s -     15.540B in   5.013476s
  Hash#fetch + block      3.099B (± 0.5%) i/s -     15.500B in   5.001211s
    Hash#fetch + arg      3.092B (± 0.9%) i/s -     15.752B in   5.094317s

Comparison:
  Hash#fetch + const: 3099687496.1 i/s
  Hash#fetch + block: 3099243342.3 i/s - same-ish: difference falls within error
    Hash#fetch + arg: 3092403282.5 i/s - same-ish: difference falls within error

$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h    30.945k i/100ms
         sort + to_h    16.635k i/100ms
Calculating -------------------------------------
      sort_by + to_h    439.544k (± 1.9%) i/s -      2.197M in   5.000381s
         sort + to_h    124.157k (± 1.9%) i/s -    632.130k in   5.093353s

Comparison:
      sort_by + to_h:   439543.9 i/s
         sort + to_h:   124157.3 i/s - 3.54x  (± 0.00) slower

$ ruby -v code/hash/keys-each-vs-each_key.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each   198.820k i/100ms
       Hash#each_key   229.566k i/100ms
Calculating -------------------------------------
      Hash#keys.each      1.992M (± 0.7%) i/s -     10.140M in   5.090246s
       Hash#each_key      2.303M (± 1.6%) i/s -     11.708M in   5.084649s

Comparison:
       Hash#each_key:  2303206.7 i/s
      Hash#keys.each:  1992115.2 i/s - 1.16x  (± 0.00) slower

$ ruby -v code/hash/keys-include-vs-key.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?   109.000  i/100ms
           Hash#key?     3.700M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      1.591k (± 5.2%) i/s -      7.957k in   5.016389s
           Hash#key?     39.278M (± 2.1%) i/s -    199.785M in   5.088566s

Comparison:
           Hash#key?: 39278290.6 i/s
  Hash#keys.include?:     1591.1 i/s - 24685.85x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-[]=.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    46.217k i/100ms
            Hash#[]=    48.874k i/100ms
Calculating -------------------------------------
         Hash#merge!    449.327k (± 0.9%) i/s -      2.265M in   5.040432s
            Hash#[]=    479.494k (± 1.0%) i/s -      2.444M in   5.096911s

Comparison:
            Hash#[]=:   479493.8 i/s
         Hash#merge!:   449327.5 i/s - 1.07x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                        25.034k i/100ms
      Hash#merge({})    14.239k i/100ms
 Hash#dup#merge!({})    22.601k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        247.398k (± 1.1%) i/s -      1.252M in   5.060050s
      Hash#merge({})    141.890k (± 0.9%) i/s -    711.950k in   5.018067s
 Hash#dup#merge!({})    228.154k (± 1.2%) i/s -      1.153M in   5.052840s

Comparison:
{}#merge!(Hash) do end:   247397.9 i/s
 Hash#dup#merge!({}):   228154.3 i/s - 1.08x  (± 0.00) slower
      Hash#merge({}):   141889.9 i/s - 1.74x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-double-splat-operator.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   286.392M i/100ms
          Hash#merge   286.501M i/100ms
Calculating -------------------------------------
        Hash#**other      2.868B (± 0.1%) i/s -     14.606B in   5.092676s
          Hash#merge      2.991B (± 2.5%) i/s -     15.185B in   5.079831s

Comparison:
          Hash#merge: 2990994018.3 i/s
        Hash#**other: 2868038376.0 i/s - 1.04x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-merge-bang.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge   810.000  i/100ms
         Hash#merge!    47.770k i/100ms
Calculating -------------------------------------
          Hash#merge      9.271k (± 1.3%) i/s -     46.980k in   5.068431s
         Hash#merge!    465.247k (± 0.8%) i/s -      2.341M in   5.031494s

Comparison:
         Hash#merge!:   465247.0 i/s
          Hash#merge:     9270.6 i/s - 50.19x  (± 0.00) slower

$ ruby -v code/hash/slice-native-vs-before-native.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice        1.594M i/100ms
Array#each               1.270M i/100ms
Array#each_w/_object     1.271M i/100ms
Hash#select-include      2.065M i/100ms
Calculating -------------------------------------
Hash#native-slice        15.932M (± 0.5%) i/s -     79.688M in   5.001906s
Array#each               13.036M (± 1.2%) i/s -     66.041M in   5.066821s
Array#each_w/_object     13.362M (± 1.6%) i/s -     67.344M in   5.041313s
Hash#select-include      22.377M (± 1.1%) i/s -    113.554M in   5.075268s

Comparison:
Hash#select-include : 22376751.7 i/s
Hash#native-slice   : 15932045.2 i/s - 1.40x  (± 0.00) slower
Array#each_w/_object: 13361572.3 i/s - 1.67x  (± 0.00) slower
Array#each          : 13035835.7 i/s - 1.72x  (± 0.00) slower

$ ruby -v code/hash/values-include-vs-value.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?   104.000  i/100ms
         Hash#value?     1.031k i/100ms
Calculating -------------------------------------
Hash#values.include?      1.533k (± 4.6%) i/s -      7.696k in   5.033304s
         Hash#value?     10.641k (± 2.5%) i/s -     53.612k in   5.041532s

Comparison:
         Hash#value?:    10640.7 i/s
Hash#values.include?:     1532.8 i/s - 6.94x  (± 0.00) slower

$ ruby -v code/method/call-vs-send-vs-method_missing.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   302.176M i/100ms
                send   302.533M i/100ms
      method_missing   302.788M i/100ms
Calculating -------------------------------------
                call      3.025B (± 0.2%) i/s -     15.411B in   5.094094s
                send      3.052B (± 1.2%) i/s -     15.429B in   5.056050s
      method_missing      3.092B (± 1.1%) i/s -     15.745B in   5.092124s

Comparison:
      method_missing: 3092384771.8 i/s
                send: 3052047882.9 i/s - same-ish: difference falls within error
                call: 3025273830.4 i/s - 1.02x  (± 0.00) slower

$ ruby -v code/proc-and-block/block-vs-to_proc.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    66.230k i/100ms
      Symbol#to_proc    65.067k i/100ms
Calculating -------------------------------------
               Block    655.611k (± 1.2%) i/s -      3.312M in   5.051805s
      Symbol#to_proc    650.551k (± 1.3%) i/s -      3.253M in   5.001722s

Comparison:
               Block:   655611.2 i/s
      Symbol#to_proc:   650551.3 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   179.372M i/100ms
       block + yield   179.133M i/100ms
        unused block   179.296M i/100ms
               yield   179.339M i/100ms
Calculating -------------------------------------
          block.call      1.853B (± 1.9%) i/s -      9.327B in   5.035048s
       block + yield      1.934B (± 0.7%) i/s -      9.673B in   5.001103s
        unused block      1.937B (± 0.6%) i/s -      9.861B in   5.090537s
               yield      1.938B (± 0.6%) i/s -      9.864B in   5.090401s

Comparison:
               yield: 1937761070.0 i/s
        unused block: 1937237226.8 i/s - same-ish: difference falls within error
       block + yield: 1934315784.7 i/s - same-ish: difference falls within error
          block.call: 1853136041.9 i/s - 1.05x  (± 0.00) slower

$ ruby -v code/range/cover-vs-include.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?     5.916M i/100ms
      range#include?    24.278k i/100ms
       range#member?    42.404k i/100ms
       plain compare     6.361M i/100ms
Calculating -------------------------------------
        range#cover?     47.785M (±11.7%) i/s -    236.653M in   5.088244s
      range#include?    342.927k (± 0.7%) i/s -      1.724M in   5.026810s
       range#member?    342.288k (± 0.8%) i/s -      1.739M in   5.079534s
       plain compare     61.924M (± 0.8%) i/s -    311.688M in   5.033706s

Comparison:
       plain compare: 61924384.2 i/s
        range#cover?: 47784660.4 i/s - 1.30x  (± 0.00) slower
      range#include?:   342927.2 i/s - 180.58x  (± 0.00) slower
       range#member?:   342288.4 i/s - 180.91x  (± 0.00) slower

$ ruby -v code/string/===-vs-=~-vs-match.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     1.212M i/100ms
           String#=~     1.209M i/100ms
          Regexp#===     1.210M i/100ms
        String#match     1.166M i/100ms
Calculating -------------------------------------
       String#match?     11.961M (± 0.7%) i/s -     60.582M in   5.065085s
           String#=~     11.885M (± 2.4%) i/s -     60.467M in   5.090701s
          Regexp#===     11.630M (± 0.6%) i/s -     59.271M in   5.096776s
        String#match     11.480M (± 0.6%) i/s -     58.294M in   5.078183s

Comparison:
       String#match?: 11961153.2 i/s
           String#=~: 11885123.8 i/s - same-ish: difference falls within error
          Regexp#===: 11629569.2 i/s - 1.03x  (± 0.00) slower
        String#match: 11479773.4 i/s - 1.04x  (± 0.00) slower

$ ruby -v code/string/casecmp-vs-downcase-==.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.559M i/100ms
      String#casecmp     3.760M i/100ms
Calculating -------------------------------------
String#downcase + ==     26.184M (± 0.7%) i/s -    133.077M in   5.082640s
      String#casecmp     38.735M (± 1.5%) i/s -    195.537M in   5.049154s

Comparison:
      String#casecmp: 38735117.6 i/s
String#downcase + ==: 26184050.4 i/s - 1.48x  (± 0.00) slower

$ ruby -v code/string/concatenation.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   285.769M i/100ms
       String#concat   286.037M i/100ms
       String#append   284.013M i/100ms
         "foo" "bar"   286.809M i/100ms
  "#{'foo'}#{'bar'}"   286.634M i/100ms
Calculating -------------------------------------
            String#+      2.992B (± 1.4%) i/s -     15.146B in   5.063670s
       String#concat      3.049B (± 1.6%) i/s -     15.446B in   5.067730s
       String#append      3.080B (± 1.0%) i/s -     15.621B in   5.072110s
         "foo" "bar"      3.096B (± 0.7%) i/s -     15.488B in   5.002596s
  "#{'foo'}#{'bar'}"      3.079B (± 1.3%) i/s -     15.478B in   5.027778s

Comparison:
         "foo" "bar": 3096089159.7 i/s
       String#append: 3080066322.3 i/s - same-ish: difference falls within error
  "#{'foo'}#{'bar'}": 3079082086.5 i/s - same-ish: difference falls within error
       String#concat: 3048680937.0 i/s - same-ish: difference falls within error
            String#+: 2991622165.9 i/s - 1.03x  (± 0.00) slower

$ ruby -v code/string/dup-vs-unary-plus.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   307.564M i/100ms
          String#dup   307.231M i/100ms
Calculating -------------------------------------
           String#+@      3.087B (± 0.8%) i/s -     15.686B in   5.082171s
          String#dup      3.078B (± 1.0%) i/s -     15.669B in   5.090792s

Comparison:
           String#+@: 3086628583.1 i/s
          String#dup: 3078148299.1 i/s - same-ish: difference falls within error

$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   205.019k i/100ms
       String#match?   208.568k i/100ms
    String#end_with?     4.106M i/100ms
Calculating -------------------------------------
           String#=~      2.005M (± 1.9%) i/s -     10.046M in   5.013238s
       String#match?      2.083M (± 1.4%) i/s -     10.428M in   5.008050s
    String#end_with?     40.310M (± 1.3%) i/s -    205.297M in   5.093790s

Comparison:
    String#end_with?: 40310449.6 i/s
       String#match?:  2082731.8 i/s - 19.35x  (± 0.00) slower
           String#=~:  2004641.5 i/s - 20.11x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-sub.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    71.943k i/100ms
          String#sub    75.231k i/100ms
String#dup["string"]=
                         5.092M i/100ms
Calculating -------------------------------------
         String#gsub    812.760k (± 1.0%) i/s -      4.101M in   5.045931s
          String#sub    760.144k (± 1.3%) i/s -      3.837M in   5.048331s
String#dup["string"]=
                         52.936M (± 1.4%) i/s -    264.764M in   5.002526s

Comparison:
String#dup["string"]=: 52936032.9 i/s
         String#gsub:   812759.9 i/s - 65.13x  (± 0.00) slower
          String#sub:   760143.6 i/s - 69.64x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-tr.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    76.257k i/100ms
           String#tr   224.550k i/100ms
Calculating -------------------------------------
         String#gsub      2.499M (± 2.7%) i/s -     12.506M in   5.007710s
           String#tr      2.228M (± 1.0%) i/s -     11.228M in   5.040438s

Comparison:
         String#gsub:  2499221.6 i/s
           String#tr:  2227703.6 i/s - 1.12x  (± 0.00) slower

$ ruby -v code/string/mutable_vs_immutable_strings.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze   286.121M i/100ms
         With Freeze   286.931M i/100ms
Calculating -------------------------------------
      Without Freeze      2.867B (± 0.2%) i/s -     14.592B in   5.090324s
         With Freeze      2.968B (± 2.0%) i/s -     14.920B in   5.029836s

Comparison:
         With Freeze: 2967528528.8 i/s
      Without Freeze: 2866657567.1 i/s - 1.04x  (± 0.00) slower

$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/     3.730k i/100ms
      String#squeeze    54.299k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     51.603k (± 2.0%) i/s -    261.100k in   5.061889s
      String#squeeze    517.856k (± 1.1%) i/s -      2.606M in   5.033543s

Comparison:
      String#squeeze:   517855.9 i/s
 String#gsub/regex+/:    51602.7 i/s - 10.04x  (± 0.00) slower

$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   583.844k i/100ms
       String#match?   588.451k i/100ms
  String#start_with?     2.665M i/100ms
Calculating -------------------------------------
           String#=~      5.852M (± 0.6%) i/s -     29.776M in   5.088726s
       String#match?      5.974M (± 1.2%) i/s -     30.011M in   5.024518s
  String#start_with?     26.645M (± 0.8%) i/s -    133.233M in   5.000629s

Comparison:
  String#start_with?: 26644877.4 i/s
       String#match?:  5973769.9 i/s - 4.46x  (± 0.00) slower
           String#=~:  5851608.8 i/s - 4.55x  (± 0.00) slower

$ ruby -v code/string/start_with-vs-substring-==.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?   255.193k i/100ms
    String#[0, n] ==   148.352k i/100ms
   String#[RANGE] ==   194.283k i/100ms
   String#[0...n] ==   496.270k i/100ms
Calculating -------------------------------------
  String#start_with?      6.336M (± 1.7%) i/s -     31.899M in   5.036280s
    String#[0, n] ==      6.499M (± 0.9%) i/s -     32.489M in   4.999526s
   String#[RANGE] ==      5.402M (± 2.7%) i/s -     27.005M in   5.003353s
   String#[0...n] ==      5.150M (± 2.3%) i/s -     25.806M in   5.013983s

Comparison:
    String#[0, n] ==:  6498933.7 i/s
  String#start_with?:  6335692.7 i/s - 1.03x  (± 0.00) slower
   String#[RANGE] ==:  5401518.0 i/s - 1.20x  (± 0.00) slower
   String#[0...n] ==:  5149590.6 i/s - 1.26x  (± 0.00) slower

$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=     5.640M i/100ms
 String#sub!'string'    79.896k i/100ms
String#gsub!'string'    84.482k i/100ms
  String#[/regexp/]=   490.042k i/100ms
 String#sub!/regexp/   585.876k i/100ms
String#gsub!/regexp/   205.300k i/100ms
Calculating -------------------------------------
  String#['string']=     54.841M (± 0.5%) i/s -    276.372M in   5.039609s
 String#sub!'string'    775.129k (± 1.3%) i/s -      3.915M in   5.051478s
String#gsub!'string'    818.877k (± 1.1%) i/s -      4.140M in   5.055844s
  String#[/regexp/]=      4.887M (± 1.7%) i/s -     24.502M in   5.014646s
 String#sub!/regexp/      5.829M (± 0.9%) i/s -     29.294M in   5.025612s
String#gsub!/regexp/      2.192M (± 0.6%) i/s -     11.086M in   5.057290s

Comparison:
  String#['string']=: 54841096.9 i/s
 String#sub!/regexp/:  5829336.7 i/s - 9.41x  (± 0.00) slower
  String#[/regexp/]=:  4887473.4 i/s - 11.22x  (± 0.00) slower
String#gsub!/regexp/:  2192202.8 i/s - 25.02x  (± 0.00) slower
String#gsub!'string':   818877.0 i/s - 66.97x  (± 0.00) slower
 String#sub!'string':   775129.3 i/s - 70.75x  (± 0.00) slower

$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub   516.973k i/100ms
        String#chomp     4.520M i/100ms
String#delete_suffix     5.119M i/100ms
Calculating -------------------------------------
          String#sub      5.153M (± 1.3%) i/s -     25.849M in   5.016710s
        String#chomp     44.962M (± 0.9%) i/s -    225.981M in   5.026419s
String#delete_suffix     51.079M (± 0.4%) i/s -    255.942M in   5.010822s

Comparison:
String#delete_suffix: 51078793.7 i/s
        String#chomp: 44961964.9 i/s - 1.14x  (± 0.00) slower
          String#sub:  5153451.6 i/s - 9.91x  (± 0.00) slower

$ ruby -v code/string/sub-vs-delete_prefix.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     3.543M i/100ms
          String#sub   606.765k i/100ms
Calculating -------------------------------------
String#delete_prefix     34.720M (± 2.1%) i/s -    177.130M in   5.104049s
          String#sub      5.617M (± 1.6%) i/s -     28.518M in   5.078085s

Comparison:
String#delete_prefix: 34719654.3 i/s
          String#sub:  5617421.0 i/s - 6.18x  (± 0.00) slower

$ ruby -v code/string/unpack1-vs-unpack[0].rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     1.737M i/100ms
    String#unpack[0]     1.786M i/100ms
Calculating -------------------------------------
      String#unpack1     17.776M (± 1.4%) i/s -     90.345M in   5.083282s
    String#unpack[0]     18.434M (± 2.7%) i/s -     92.878M in   5.042279s

Comparison:
    String#unpack[0]: 18433640.2 i/s
      String#unpack1: 17776445.8 i/s - same-ish: difference falls within error

$ ruby -v code/time/iso8601-vs-parse.rb
truffleruby 21.1.0-dev-e0ef0b27, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601    17.753k i/100ms
          Time.parse     2.542k i/100ms
Calculating -------------------------------------
        Time.iso8601    265.696k (± 2.4%) i/s -      1.331M in   5.014176s
          Time.parse     31.082k (± 7.0%) i/s -    155.062k in   5.021732s

Comparison:
        Time.iso8601:   265696.5 i/s
          Time.parse:    31082.2 i/s - 8.55x  (± 0.00) slower

rake  1670.79s user 33.25s system 140% cpu 20:13.24 total

```



## License

![CC-BY-SA](CC-BY-SA.png)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Code License

### CC0 1.0 Universal

To the extent possible under law, @JuanitoFatas has waived all copyright and related or neighboring rights to "fast-ruby".

This work belongs to the community.
