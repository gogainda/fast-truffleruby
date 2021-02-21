## Fast TruffleRuby 


The idea of this project is to run all collected examples from [Fast Ruby](https://github.com/JuanitoFatas/fast-ruby) and run it against the latest TruffleRuby version to see if the same results hold for the TruffleRuby.

As you will see in the results below, some results a quite different

## Results
```
$ ruby -v code/general/array-argument-vs-splat-arguments.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       329.303M i/100ms
Function with splat arguments
                         1.336k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          3.208B (± 6.5%) i/s -     16.136B in   5.052772s
Function with splat arguments
                         17.253k (± 3.0%) i/s -     86.840k in   5.037878s

Comparison:
Function with single Array argument: 3207812598.8 i/s
Function with splat arguments:    17253.3 i/s - 185924.42x  (± 0.00) slower

$ ruby -v code/general/assignment.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   351.290M i/100ms
Sequential Assignment
                       362.239M i/100ms
Calculating -------------------------------------
 Parallel Assignment      3.627B (± 1.7%) i/s -     18.267B in   5.038553s
Sequential Assignment
                          3.593B (± 2.0%) i/s -     18.112B in   5.043406s

Comparison:
 Parallel Assignment: 3626601707.4 i/s
Sequential Assignment: 3592683688.6 i/s - same-ish: difference falls within error

$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   358.546M i/100ms
       attr_accessor   362.488M i/100ms
Calculating -------------------------------------
   getter_and_setter      3.618B (± 1.9%) i/s -     18.286B in   5.055663s
       attr_accessor      3.632B (± 1.5%) i/s -     18.487B in   5.091444s

Comparison:
       attr_accessor: 3631804374.9 i/s
   getter_and_setter: 3618238706.1 i/s - same-ish: difference falls within error

$ ruby -v code/general/begin-rescue-vs-respond-to.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     9.980k i/100ms
         respond_to?   366.706M i/100ms
Calculating -------------------------------------
      begin...rescue     99.459k (± 1.2%) i/s -    499.000k in   5.017876s
         respond_to?      3.643B (± 2.5%) i/s -     18.335B in   5.036924s

Comparison:
         respond_to?: 3642784886.3 i/s
      begin...rescue:    99459.0 i/s - 36625.98x  (± 0.00) slower

$ ruby -v code/general/block-apply-method.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   367.131M i/100ms
             &method   367.552M i/100ms
Calculating -------------------------------------
              normal      3.656B (± 1.0%) i/s -     18.357B in   5.020924s
             &method      3.595B (± 4.7%) i/s -     18.010B in   5.022168s

Comparison:
              normal: 3656378729.5 i/s
             &method: 3594936137.1 i/s - same-ish: difference falls within error

$ ruby -v code/general/define_method-vs-module-eval.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                       185.000  i/100ms
       define_method   151.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.645k (±34.2%) i/s -      6.105k in   5.034318s
       define_method      4.554k (±36.6%) i/s -     16.157k in   5.021952s

Comparison:
       define_method:     4553.5 i/s
module_eval with string:     1644.8 i/s - 2.77x  (± 0.00) slower

$ ruby -v code/general/format-vs-round-and-to-s.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    56.989k i/100ms
       Kernel#format    79.263k i/100ms
            String#%    78.755k i/100ms
Calculating -------------------------------------
         Float#round    576.558k (± 3.0%) i/s -      2.906M in   5.045634s
       Kernel#format    781.503k (± 0.8%) i/s -      3.963M in   5.071521s
            String#%    782.010k (± 1.1%) i/s -      3.938M in   5.036001s

Comparison:
            String#%:   782009.5 i/s
       Kernel#format:   781503.1 i/s - same-ish: difference falls within error
         Float#round:   576558.2 i/s - 1.36x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct-on-access.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   362.039M i/100ms
          OpenStruct    75.665M i/100ms
Calculating -------------------------------------
                Hash      3.638B (± 1.0%) i/s -     18.464B in   5.076197s
          OpenStruct    762.756M (± 0.9%) i/s -      3.859B in   5.059542s

Comparison:
                Hash: 3637709117.1 i/s
          OpenStruct: 762755846.1 i/s - 4.77x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   365.884M i/100ms
          OpenStruct   368.816M i/100ms
Calculating -------------------------------------
                Hash      3.675B (± 1.6%) i/s -     18.660B in   5.078438s
          OpenStruct      3.665B (± 1.6%) i/s -     18.441B in   5.032325s

Comparison:
                Hash: 3675341244.1 i/s
          OpenStruct: 3665484935.7 i/s - same-ish: difference falls within error

$ ruby -v code/general/inheritance-check.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal     1.360M i/100ms
  ancestors.include?   208.889k i/100ms
Calculating -------------------------------------
  less than or equal     13.880M (± 1.3%) i/s -     69.376M in   4.999262s
  ancestors.include?      2.131M (± 1.4%) i/s -     10.862M in   5.098152s

Comparison:
  less than or equal: 13879816.6 i/s
  ancestors.include?:  2131037.8 i/s - 6.51x  (± 0.00) slower

$ ruby -v code/general/loop-vs-while-true.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     3.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     36.151  (± 5.5%) i/s -    183.000  in   5.072407s
         Kernel loop      9.183  (± 0.0%) i/s -     46.000  in   5.013167s

Comparison:
          While Loop:       36.2 i/s
         Kernel loop:        9.2 i/s - 3.94x  (± 0.00) slower

$ ruby -v code/array/array-first-vs-index.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   202.965M i/100ms
         Array#first   207.999M i/100ms
Calculating -------------------------------------
           Array#[0]      2.292B (± 2.8%) i/s -     11.569B in   5.052385s
         Array#first      2.221B (± 5.3%) i/s -     11.232B in   5.071405s

Comparison:
           Array#[0]: 2291746837.7 i/s
         Array#first: 2221050201.8 i/s - same-ish: difference falls within error

$ ruby -v code/array/array-last-vs-index.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   305.210M i/100ms
          Array#last   368.074M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.604B (± 4.2%) i/s -     18.007B in   5.005682s
          Array#last      3.601B (± 3.8%) i/s -     18.036B in   5.015451s

Comparison:
          Array#[-1]: 3603905067.0 i/s
          Array#last: 3601368980.4 i/s - same-ish: difference falls within error

$ ruby -v code/array/bsearch-vs-find.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   475.661k i/100ms
Calculating -------------------------------------
                find      0.114  (± 0.0%) i/s -      1.000  in   8.744843s
             bsearch      4.439M (±12.6%) i/s -     22.356M in   5.151882s

Comparison:
             bsearch:  4438566.5 i/s
                find:        0.1 i/s - 38814567.52x  (± 0.00) slower

$ ruby -v code/array/insert-vs-unshift.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.172  (± 0.0%) i/s -      1.000  in   5.827282s
        Array#insert      0.314  (± 0.0%) i/s -      2.000  in   6.367047s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.83x  (± 0.00) slower

$ ruby -v code/array/length-vs-size-vs-count.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   339.988M i/100ms
          Array#size   375.220M i/100ms
         Array#count   371.086M i/100ms
Calculating -------------------------------------
        Array#length      3.611B (± 4.4%) i/s -     18.359B in   5.094929s
          Array#size      3.539B (± 4.8%) i/s -     18.011B in   5.100751s
         Array#count      3.580B (± 5.6%) i/s -     18.183B in   5.096410s

Comparison:
        Array#length: 3610918175.4 i/s
         Array#count: 3579746217.7 i/s - same-ish: difference falls within error
          Array#size: 3539094356.9 i/s - same-ish: difference falls within error

$ ruby -v code/array/shuffle-first-vs-sample.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    33.741k i/100ms
        Array#sample     3.493M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    343.314k (± 3.2%) i/s -      1.721M in   5.017206s
        Array#sample     35.650M (± 3.9%) i/s -    178.156M in   5.004890s

Comparison:
        Array#sample: 35649775.7 i/s
 Array#shuffle.first:   343314.0 i/s - 103.84x  (± 0.00) slower

$ ruby -v code/date/iso8601-vs-parse.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601     2.312k i/100ms
          Date.parse     2.835k i/100ms
Calculating -------------------------------------
        Date.iso8601     39.120k (±15.4%) i/s -    191.896k in   5.034168s
          Date.parse     50.374k (± 7.1%) i/s -    252.315k in   5.035189s

Comparison:
          Date.parse:    50374.0 i/s
        Date.iso8601:    39119.8 i/s - 1.29x  (± 0.00) slower

$ ruby -v code/enumerable/each-push-vs-map.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   353.882k i/100ms
           Array#map     1.408M i/100ms
Calculating -------------------------------------
   Array#each + push      3.649M (± 4.7%) i/s -     18.402M in   5.053632s
           Array#map     13.591M (± 6.1%) i/s -     68.988M in   5.095557s

Comparison:
           Array#map: 13590694.4 i/s
   Array#each + push:  3649365.2 i/s - 3.72x  (± 0.00) slower

$ ruby -v code/enumerable/each-vs-for-loop.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop     1.221M i/100ms
               #each     1.226M i/100ms
Calculating -------------------------------------
            For loop     12.945M (± 3.5%) i/s -     64.709M in   5.004941s
               #each     12.769M (± 4.7%) i/s -     63.746M in   5.002949s

Comparison:
            For loop: 12945361.7 i/s
               #each: 12769370.9 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   499.646k i/100ms
     each_with_index   988.250k i/100ms
Calculating -------------------------------------
          While Loop      5.230M (± 3.7%) i/s -     26.481M in   5.070356s
     each_with_index      9.842M (± 4.5%) i/s -     49.413M in   5.030880s

Comparison:
     each_with_index:  9841563.9 i/s
          While Loop:  5230056.7 i/s - 1.88x  (± 0.00) slower

$ ruby -v code/enumerable/inject-symbol-vs-block.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   209.130k i/100ms
      inject to_proc   208.999k i/100ms
        inject block   226.940k i/100ms
Calculating -------------------------------------
       inject symbol      2.160M (± 4.5%) i/s -     10.875M in   5.043670s
      inject to_proc      2.171M (± 4.2%) i/s -     10.868M in   5.014501s
        inject block      2.152M (± 6.1%) i/s -     10.893M in   5.081245s

Comparison:
      inject to_proc:  2171204.2 i/s
       inject symbol:  2160376.7 i/s - same-ish: difference falls within error
        inject block:  2152127.3 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    22.889k i/100ms
   Array#map.flatten    22.159k i/100ms
      Array#flat_map    59.865k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    238.730k (± 5.1%) i/s -      1.213M in   5.094707s
   Array#map.flatten    233.926k (± 4.6%) i/s -      1.174M in   5.031261s
      Array#flat_map    552.326k (± 5.2%) i/s -      2.814M in   5.107486s

Comparison:
      Array#flat_map:   552326.3 i/s
Array#map.flatten(1):   238729.7 i/s - 2.31x  (± 0.00) slower
   Array#map.flatten:   233926.2 i/s - 2.36x  (± 0.00) slower

$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   236.950k i/100ms
  Array#reverse_each   602.065k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.466M (± 5.6%) i/s -     12.321M in   5.012436s
  Array#reverse_each      6.012M (± 4.0%) i/s -     30.103M in   5.015654s

Comparison:
  Array#reverse_each:  6012054.2 i/s
  Array#reverse.each:  2465900.8 i/s - 2.44x  (± 0.00) slower

$ ruby -v code/enumerable/select-first-vs-detect.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       718.117k i/100ms
   Enumerable#detect     4.258M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          7.379M (± 4.8%) i/s -    147.932M in  20.093763s
   Enumerable#detect     44.235M (± 3.7%) i/s -    885.766M in  20.051707s

Comparison:
   Enumerable#detect: 44234605.3 i/s
Enumerable#select.first:  7378942.3 i/s - 5.99x  (± 0.00) slower

$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       245.239k i/100ms
Enumerable#select.last
                       375.111k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.620M (± 6.0%) i/s -     13.243M in   5.073640s
Enumerable#select.last
                          3.893M (± 4.7%) i/s -     19.506M in   5.021646s

Comparison:
Enumerable#select.last:  3892993.4 i/s
Enumerable#reverse.detect:  2619716.7 i/s - 1.49x  (± 0.00) slower

$ ruby -v code/enumerable/sort-vs-sort_by.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         4.230k i/100ms
  Enumerable#sort_by     4.181k i/100ms
     Enumerable#sort     5.153k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         50.443k (±10.3%) i/s -    249.570k in   5.009318s
  Enumerable#sort_by     50.263k (± 9.6%) i/s -    250.860k in   5.045060s
     Enumerable#sort     74.497k (± 5.3%) i/s -    376.169k in   5.064471s

Comparison:
     Enumerable#sort:    74497.4 i/s
Enumerable#sort_by (Symbol#to_proc):    50443.5 i/s - 1.48x  (± 0.00) slower
  Enumerable#sort_by:    50263.3 i/s - 1.48x  (± 0.00) slower

$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   336.853k i/100ms
Enumerable#sort_by...first
                         9.441k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      3.500M (± 3.5%) i/s -     17.516M in   5.010878s
Enumerable#sort_by...first
                        114.621k (± 4.7%) i/s -    575.901k in   5.035313s

Comparison:
   Enumerable#min_by:  3499978.7 i/s
Enumerable#sort_by...first:   114621.1 i/s - 30.54x  (± 0.00) slower

$ ruby -v code/hash/bracket-vs-dup.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   613.240k i/100ms
            Hash#dup   601.722k i/100ms
Calculating -------------------------------------
              Hash[]      6.325M (± 4.7%) i/s -     31.888M in   5.052467s
            Hash#dup      6.195M (± 4.6%) i/s -     31.290M in   5.061757s

Comparison:
              Hash[]:  6325431.1 i/s
            Hash#dup:  6194627.4 i/s - same-ish: difference falls within error

$ ruby -v code/hash/bracket-vs-fetch.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   333.333M i/100ms
  Hash#fetch, symbol   231.391M i/100ms
     Hash#[], string    12.068M i/100ms
  Hash#fetch, string     9.755M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      3.613B (± 4.6%) i/s -     18.333B in   5.085603s
  Hash#fetch, symbol      2.281B (± 3.8%) i/s -     11.570B in   5.079590s
     Hash#[], string    119.560M (± 2.0%) i/s -    603.410M in   5.048987s
  Hash#fetch, string     94.439M (± 5.2%) i/s -    478.001M in   5.075937s

Comparison:
     Hash#[], symbol: 3613069633.6 i/s
  Hash#fetch, symbol: 2281090273.4 i/s - 1.58x  (± 0.00) slower
     Hash#[], string: 119559857.1 i/s - 30.22x  (± 0.00) slower
  Hash#fetch, string: 94439463.5 i/s - 38.26x  (± 0.00) slower

$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig   910.873k i/100ms
             Hash#[]     5.765M i/100ms
          Hash#[] ||     6.053M i/100ms
          Hash#[] &&     5.965M i/100ms
          Hash#fetch     5.431M i/100ms
 Hash#fetch fallback     5.339M i/100ms
Calculating -------------------------------------
            Hash#dig      9.545M (± 4.4%) i/s -     48.276M in   5.067664s
             Hash#[]     59.829M (± 3.2%) i/s -    299.768M in   5.015580s
          Hash#[] ||     59.315M (± 3.5%) i/s -    296.589M in   5.006385s
          Hash#[] &&     59.378M (± 3.5%) i/s -    298.273M in   5.029470s
          Hash#fetch     57.118M (± 3.4%) i/s -    287.859M in   5.045688s
 Hash#fetch fallback     57.534M (± 3.8%) i/s -    288.287M in   5.018315s

Comparison:
             Hash#[]: 59829471.0 i/s
          Hash#[] &&: 59377880.5 i/s - same-ish: difference falls within error
          Hash#[] ||: 59314721.0 i/s - same-ish: difference falls within error
 Hash#fetch fallback: 57534375.5 i/s - same-ish: difference falls within error
          Hash#fetch: 57117935.5 i/s - same-ish: difference falls within error
            Hash#dig:  9544769.9 i/s - 6.27x  (± 0.00) slower

$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   342.824M i/100ms
  Hash#fetch + block   338.592M i/100ms
    Hash#fetch + arg   370.246M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      3.551B (± 5.7%) i/s -     17.827B in   5.038326s
  Hash#fetch + block      3.604B (± 4.0%) i/s -     18.284B in   5.082272s
    Hash#fetch + arg      3.668B (± 3.4%) i/s -     18.512B in   5.052732s

Comparison:
    Hash#fetch + arg: 3668295371.6 i/s
  Hash#fetch + block: 3603730956.2 i/s - same-ish: difference falls within error
  Hash#fetch + const: 3550738279.9 i/s - same-ish: difference falls within error

$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h    32.985k i/100ms
         sort + to_h     7.621k i/100ms
Calculating -------------------------------------
      sort_by + to_h    284.735k (± 9.3%) i/s -      1.418M in   5.053915s
         sort + to_h     77.924k (± 5.4%) i/s -    388.671k in   5.003107s

Comparison:
      sort_by + to_h:   284734.9 i/s
         sort + to_h:    77923.6 i/s - 3.65x  (± 0.00) slower

$ ruby -v code/hash/keys-each-vs-each_key.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each   242.619k i/100ms
       Hash#each_key   296.005k i/100ms
Calculating -------------------------------------
      Hash#keys.each      2.517M (± 4.1%) i/s -     12.616M in   5.020123s
       Hash#each_key      2.843M (± 5.0%) i/s -     14.208M in   5.010974s

Comparison:
       Hash#each_key:  2842774.9 i/s
      Hash#keys.each:  2517315.2 i/s - 1.13x  (± 0.00) slower

$ ruby -v code/hash/keys-include-vs-key.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?    87.000  i/100ms
           Hash#key?    10.948M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      2.519k (±33.3%) i/s -     11.484k in   5.004644s
           Hash#key?    117.516M (± 3.3%) i/s -    591.209M in   5.036538s

Comparison:
           Hash#key?: 117515829.6 i/s
  Hash#keys.include?:     2519.2 i/s - 46647.81x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-[]=.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    55.755k i/100ms
            Hash#[]=    50.256k i/100ms
Calculating -------------------------------------
         Hash#merge!    597.387k (± 6.4%) i/s -      3.011M in   5.061065s
            Hash#[]=    561.298k (± 6.5%) i/s -      2.814M in   5.035308s

Comparison:
         Hash#merge!:   597386.9 i/s
            Hash#[]=:   561298.0 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                        28.672k i/100ms
      Hash#merge({})    17.537k i/100ms
 Hash#dup#merge!({})    25.535k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        296.976k (± 5.2%) i/s -      1.491M in   5.034450s
      Hash#merge({})    179.211k (± 6.5%) i/s -    894.387k in   5.012425s
 Hash#dup#merge!({})    264.396k (± 7.3%) i/s -      1.328M in   5.050665s

Comparison:
{}#merge!(Hash) do end:   296975.5 i/s
 Hash#dup#merge!({}):   264396.2 i/s - same-ish: difference falls within error
      Hash#merge({}):   179211.4 i/s - 1.66x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-double-splat-operator.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   322.055M i/100ms
          Hash#merge   368.312M i/100ms
Calculating -------------------------------------
        Hash#**other      3.609B (± 4.0%) i/s -     18.035B in   5.006096s
          Hash#merge      3.608B (± 4.6%) i/s -     18.047B in   5.012906s

Comparison:
        Hash#**other: 3608822270.8 i/s
          Hash#merge: 3608256049.3 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-vs-merge-bang.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge   924.000  i/100ms
         Hash#merge!    53.462k i/100ms
Calculating -------------------------------------
          Hash#merge      9.866k (± 5.3%) i/s -     49.896k in   5.071813s
         Hash#merge!    559.407k (± 5.2%) i/s -      2.833M in   5.078636s

Comparison:
         Hash#merge!:   559406.9 i/s
          Hash#merge:     9866.1 i/s - 56.70x  (± 0.00) slower

$ ruby -v code/hash/slice-native-vs-before-native.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice        1.828M i/100ms
Array#each               1.666M i/100ms
Array#each_w/_object     1.561M i/100ms
Hash#select-include      2.351M i/100ms
Calculating -------------------------------------
Hash#native-slice        19.408M (± 5.7%) i/s -     96.885M in   5.008693s
Array#each               16.091M (± 5.4%) i/s -     81.621M in   5.088022s
Array#each_w/_object     15.845M (± 5.8%) i/s -     79.635M in   5.043208s
Hash#select-include      24.473M (± 5.5%) i/s -    122.267M in   5.011147s

Comparison:
Hash#select-include : 24472751.5 i/s
Hash#native-slice   : 19407515.1 i/s - 1.26x  (± 0.00) slower
Array#each          : 16091047.0 i/s - 1.52x  (± 0.00) slower
Array#each_w/_object: 15845210.0 i/s - 1.54x  (± 0.00) slower

$ ruby -v code/hash/values-include-vs-value.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?    90.000  i/100ms
         Hash#value?   378.000  i/100ms
Calculating -------------------------------------
Hash#values.include?      2.462k (±29.3%) i/s -     11.430k in   5.005810s
         Hash#value?      8.235k (±18.9%) i/s -     38.556k in   5.032474s

Comparison:
         Hash#value?:     8235.4 i/s
Hash#values.include?:     2462.2 i/s - 3.34x  (± 0.00) slower

$ ruby -v code/method/call-vs-send-vs-method_missing.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   372.206M i/100ms
                send   341.496M i/100ms
      method_missing   367.883M i/100ms
Calculating -------------------------------------
                call      3.476B (± 6.1%) i/s -     17.494B in   5.053034s
                send      3.589B (± 4.9%) i/s -     18.099B in   5.055994s
      method_missing      3.633B (± 3.4%) i/s -     18.394B in   5.068918s

Comparison:
      method_missing: 3633338027.4 i/s
                send: 3589088418.6 i/s - same-ish: difference falls within error
                call: 3475567195.0 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/block-vs-to_proc.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    68.572k i/100ms
      Symbol#to_proc    70.113k i/100ms
Calculating -------------------------------------
               Block    716.412k (± 1.8%) i/s -      3.634M in   5.074710s
      Symbol#to_proc    710.889k (± 1.6%) i/s -      3.576M in   5.031286s

Comparison:
               Block:   716411.8 i/s
      Symbol#to_proc:   710889.4 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   233.356M i/100ms
       block + yield   231.279M i/100ms
        unused block   212.217M i/100ms
               yield   227.122M i/100ms
Calculating -------------------------------------
          block.call      2.271B (± 4.2%) i/s -     11.434B in   5.043731s
       block + yield      2.323B (± 0.5%) i/s -     11.795B in   5.077218s
        unused block      2.270B (± 3.9%) i/s -     11.460B in   5.056968s
               yield      2.252B (± 4.4%) i/s -     11.356B in   5.053439s

Comparison:
       block + yield: 2323227961.6 i/s
          block.call: 2271254198.0 i/s - same-ish: difference falls within error
        unused block: 2269682715.9 i/s - same-ish: difference falls within error
               yield: 2251778434.3 i/s - same-ish: difference falls within error

$ ruby -v code/range/cover-vs-include.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?     6.742M i/100ms
      range#include?    14.333k i/100ms
       range#member?    20.506k i/100ms
       plain compare     6.957M i/100ms
Calculating -------------------------------------
        range#cover?     51.995M (±11.9%) i/s -    256.193M in   5.047706s
      range#include?    196.481k (± 6.1%) i/s -    988.977k in   5.052127s
       range#member?    195.537k (± 5.7%) i/s -    984.288k in   5.050387s
       plain compare     70.148M (± 5.7%) i/s -    354.795M in   5.074965s

Comparison:
       plain compare: 70148113.9 i/s
        range#cover?: 51994678.2 i/s - 1.35x  (± 0.00) slower
      range#include?:   196481.1 i/s - 357.02x  (± 0.00) slower
       range#member?:   195536.6 i/s - 358.75x  (± 0.00) slower

$ ruby -v code/string/===-vs-=~-vs-match.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     1.457M i/100ms
           String#=~     1.436M i/100ms
          Regexp#===     1.450M i/100ms
        String#match     1.548M i/100ms
Calculating -------------------------------------
       String#match?     14.865M (± 4.4%) i/s -     74.292M in   5.007307s
           String#=~     15.010M (± 4.6%) i/s -     76.108M in   5.081239s
          Regexp#===     15.067M (± 3.9%) i/s -     75.398M in   5.011726s
        String#match     14.308M (± 5.5%) i/s -     72.744M in   5.099388s

Comparison:
          Regexp#===: 15067421.8 i/s
           String#=~: 15009526.8 i/s - same-ish: difference falls within error
       String#match?: 14864702.4 i/s - same-ish: difference falls within error
        String#match: 14308263.7 i/s - same-ish: difference falls within error

$ ruby -v code/string/casecmp-vs-downcase-==.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.466M i/100ms
      String#casecmp     4.613M i/100ms
Calculating -------------------------------------
String#downcase + ==     26.658M (± 5.3%) i/s -    133.184M in   5.010411s
      String#casecmp     47.979M (± 2.9%) i/s -    239.875M in   5.003770s

Comparison:
      String#casecmp: 47979219.3 i/s
String#downcase + ==: 26657980.6 i/s - 1.80x  (± 0.00) slower

$ ruby -v code/string/concatenation.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   342.827M i/100ms
       String#concat   337.280M i/100ms
       String#append   368.508M i/100ms
         "foo" "bar"   372.798M i/100ms
  "#{'foo'}#{'bar'}"   334.528M i/100ms
Calculating -------------------------------------
            String#+      3.580B (± 4.4%) i/s -     18.170B in   5.085537s
       String#concat      3.609B (± 4.5%) i/s -     18.213B in   5.056680s
       String#append      3.627B (± 3.9%) i/s -     18.425B in   5.087933s
         "foo" "bar"      3.636B (± 4.1%) i/s -     18.267B in   5.033208s
  "#{'foo'}#{'bar'}"      3.544B (± 4.1%) i/s -     17.730B in   5.011496s

Comparison:
         "foo" "bar": 3635624345.8 i/s
       String#append: 3627189404.2 i/s - same-ish: difference falls within error
       String#concat: 3609371811.5 i/s - same-ish: difference falls within error
            String#+: 3579781188.4 i/s - same-ish: difference falls within error
  "#{'foo'}#{'bar'}": 3543794639.0 i/s - same-ish: difference falls within error

$ ruby -v code/string/dup-vs-unary-plus.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   342.113M i/100ms
          String#dup   363.494M i/100ms
Calculating -------------------------------------
           String#+@      3.615B (± 3.9%) i/s -     18.132B in   5.023634s
          String#dup      3.519B (± 6.1%) i/s -     17.811B in   5.082411s

Comparison:
           String#+@: 3615035603.5 i/s
          String#dup: 3518558368.1 i/s - same-ish: difference falls within error

$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   219.217k i/100ms
       String#match?   223.030k i/100ms
    String#end_with?     4.493M i/100ms
Calculating -------------------------------------
           String#=~      2.210M (± 3.6%) i/s -     11.180M in   5.064248s
       String#match?      2.269M (± 6.2%) i/s -     11.375M in   5.032637s
    String#end_with?     43.526M (± 5.1%) i/s -    220.161M in   5.071461s

Comparison:
    String#end_with?: 43526445.4 i/s
       String#match?:  2269189.1 i/s - 19.18x  (± 0.00) slower
           String#=~:  2210433.5 i/s - 19.69x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-sub.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    94.709k i/100ms
          String#sub    97.516k i/100ms
String#dup["string"]=
                         6.424M i/100ms
Calculating -------------------------------------
         String#gsub    997.719k (± 4.0%) i/s -      5.020M in   5.039271s
          String#sub    919.457k (± 5.5%) i/s -      4.583M in   5.000006s
String#dup["string"]=
                         66.540M (± 4.5%) i/s -    334.071M in   5.031184s

Comparison:
String#dup["string"]=: 66540354.9 i/s
         String#gsub:   997719.1 i/s - 66.69x  (± 0.00) slower
          String#sub:   919457.0 i/s - 72.37x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-tr.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub   242.614k i/100ms
           String#tr   254.917k i/100ms
Calculating -------------------------------------
         String#gsub      2.758M (± 5.8%) i/s -     13.829M in   5.031819s
           String#tr      2.611M (± 6.9%) i/s -     13.001M in   5.003372s

Comparison:
         String#gsub:  2757693.2 i/s
           String#tr:  2610768.2 i/s - same-ish: difference falls within error

$ ruby -v code/string/mutable_vs_immutable_strings.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze   341.692M i/100ms
         With Freeze   371.171M i/100ms
Calculating -------------------------------------
      Without Freeze      3.645B (± 3.4%) i/s -     18.451B in   5.068755s
         With Freeze      3.600B (± 4.6%) i/s -     18.187B in   5.063305s

Comparison:
      Without Freeze: 3644669447.1 i/s
         With Freeze: 3599910831.6 i/s - same-ish: difference falls within error

$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/     4.467k i/100ms
      String#squeeze    62.398k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     59.255k (± 5.2%) i/s -    299.289k in   5.064402s
      String#squeeze    670.653k (± 5.3%) i/s -      3.369M in   5.039210s

Comparison:
      String#squeeze:   670653.2 i/s
 String#gsub/regex+/:    59254.6 i/s - 11.32x  (± 0.00) slower

$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   697.071k i/100ms
       String#match?   655.150k i/100ms
  String#start_with?     3.349M i/100ms
Calculating -------------------------------------
           String#=~      7.208M (± 5.3%) i/s -     36.248M in   5.042103s
       String#match?      7.336M (± 7.3%) i/s -     36.688M in   5.028084s
  String#start_with?     31.123M (± 4.5%) i/s -    157.382M in   5.066810s

Comparison:
  String#start_with?: 31122638.8 i/s
       String#match?:  7336164.4 i/s - 4.24x  (± 0.00) slower
           String#=~:  7207993.3 i/s - 4.32x  (± 0.00) slower

$ ruby -v code/string/start_with-vs-substring-==.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?   685.548k i/100ms
    String#[0, n] ==   152.623k i/100ms
   String#[RANGE] ==   212.318k i/100ms
   String#[0...n] ==   572.129k i/100ms
Calculating -------------------------------------
  String#start_with?      6.934M (± 3.4%) i/s -     34.963M in   5.047878s
    String#[0, n] ==      7.608M (± 3.9%) i/s -     38.003M in   5.002677s
   String#[RANGE] ==      6.385M (± 4.5%) i/s -     32.060M in   5.031446s
   String#[0...n] ==      6.100M (± 5.2%) i/s -     30.895M in   5.079500s

Comparison:
    String#[0, n] ==:  7608282.0 i/s
  String#start_with?:  6934333.1 i/s - 1.10x  (± 0.00) slower
   String#[RANGE] ==:  6384742.6 i/s - 1.19x  (± 0.00) slower
   String#[0...n] ==:  6099916.2 i/s - 1.25x  (± 0.00) slower

$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=     6.475M i/100ms
 String#sub!'string'    91.821k i/100ms
String#gsub!'string'   102.150k i/100ms
  String#[/regexp/]=   587.093k i/100ms
 String#sub!/regexp/   726.995k i/100ms
String#gsub!/regexp/   213.243k i/100ms
Calculating -------------------------------------
  String#['string']=     67.901M (± 3.8%) i/s -    343.196M in   5.061570s
 String#sub!'string'    948.545k (± 5.1%) i/s -      4.775M in   5.046859s
String#gsub!'string'      1.025M (± 3.5%) i/s -      5.210M in   5.089929s
  String#[/regexp/]=      6.009M (± 5.3%) i/s -     30.529M in   5.095315s
 String#sub!/regexp/      6.611M (± 5.7%) i/s -     33.442M in   5.075364s
String#gsub!/regexp/      2.596M (± 5.7%) i/s -     13.008M in   5.027109s

Comparison:
  String#['string']=: 67901403.3 i/s
 String#sub!/regexp/:  6611407.7 i/s - 10.27x  (± 0.00) slower
  String#[/regexp/]=:  6008750.7 i/s - 11.30x  (± 0.00) slower
String#gsub!/regexp/:  2596004.2 i/s - 26.16x  (± 0.00) slower
String#gsub!'string':  1024756.2 i/s - 66.26x  (± 0.00) slower
 String#sub!'string':   948545.4 i/s - 71.58x  (± 0.00) slower

$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub   551.630k i/100ms
        String#chomp     5.450M i/100ms
String#delete_suffix     6.450M i/100ms
Calculating -------------------------------------
          String#sub      5.826M (± 4.9%) i/s -     29.236M in   5.029978s
        String#chomp     50.326M (± 5.1%) i/s -    256.170M in   5.103393s
String#delete_suffix     62.728M (± 4.3%) i/s -    316.038M in   5.047529s

Comparison:
String#delete_suffix: 62727743.6 i/s
        String#chomp: 50326361.3 i/s - 1.25x  (± 0.00) slower
          String#sub:  5826178.7 i/s - 10.77x  (± 0.00) slower

$ ruby -v code/string/sub-vs-delete_prefix.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     3.759M i/100ms
          String#sub   646.906k i/100ms
Calculating -------------------------------------
String#delete_prefix     38.789M (± 4.7%) i/s -    195.466M in   5.049987s
          String#sub      6.737M (± 5.9%) i/s -     33.639M in   5.010245s

Comparison:
String#delete_prefix: 38789443.9 i/s
          String#sub:  6737267.2 i/s - 5.76x  (± 0.00) slower

$ ruby -v code/string/unpack1-vs-unpack[0].rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     2.071M i/100ms
    String#unpack[0]     2.171M i/100ms
Calculating -------------------------------------
      String#unpack1     21.784M (± 4.8%) i/s -    109.789M in   5.051794s
    String#unpack[0]     22.393M (± 6.0%) i/s -    112.892M in   5.059918s

Comparison:
    String#unpack[0]: 22392551.6 i/s
      String#unpack1: 21783717.6 i/s - same-ish: difference falls within error

$ ruby -v code/time/iso8601-vs-parse.rb
truffleruby 21.1.0-dev-634c0ae2, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601    18.996k i/100ms
          Time.parse     2.838k i/100ms
Calculating -------------------------------------
        Time.iso8601    300.947k (±10.6%) i/s -      1.501M in   5.041639s
          Time.parse     43.157k (± 5.5%) i/s -    215.688k in   5.013932s

Comparison:
        Time.iso8601:   300947.5 i/s
          Time.parse:    43156.8 i/s - 6.97x  (± 0.00) slower

bundle exec rake  1646.13s user 32.48s system 134% cpu 20:52.39 total

```



## License

![CC-BY-SA](CC-BY-SA.png)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Code License

### CC0 1.0 Universal

To the extent possible under law, @JuanitoFatas has waived all copyright and related or neighboring rights to "fast-ruby".

This work belongs to the community.
