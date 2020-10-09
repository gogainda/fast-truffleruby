## Fast Truffle Ruby 


The idia of this project is to run all collected examples from the [Fast Ruby] (https://github.com/JuanitoFatas/fast-ruby) and run it against the latest truffle ruby version to see if the same results hold for the Truffle ruby. 

As you will see in the resalst below some results a quite different

## Results
```
$ ruby -v code/general/array-argument-vs-splat-arguments.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       206.043M i/100ms
Function with splat arguments
                         1.415k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          2.030B (± 3.0%) i/s -     10.302B in   5.080295s
Function with splat arguments
                         14.095k (± 4.5%) i/s -     70.750k in   5.030158s

Comparison:
Function with single Array argument: 2029787512.0 i/s
Function with splat arguments:    14094.7 i/s - 144011.14x  (± 0.00) slower

$ ruby -v code/general/assignment.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   199.503M i/100ms
Sequential Assignment
                       206.546M i/100ms
Calculating -------------------------------------
 Parallel Assignment      2.018B (± 5.0%) i/s -     10.175B in   5.057319s
Sequential Assignment
                          2.044B (± 3.4%) i/s -     10.327B in   5.058085s

Comparison:
Sequential Assignment: 2044168955.6 i/s
 Parallel Assignment: 2017502761.7 i/s - same-ish: difference falls within error

$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   211.070M i/100ms
       attr_accessor   210.895M i/100ms
Calculating -------------------------------------
   getter_and_setter      2.041B (± 3.4%) i/s -     10.342B in   5.073684s
       attr_accessor      2.046B (± 3.1%) i/s -     10.334B in   5.055251s

Comparison:
       attr_accessor: 2046235569.6 i/s
   getter_and_setter: 2040863966.9 i/s - same-ish: difference falls within error

$ ruby -v code/general/begin-rescue-vs-respond-to.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     8.850k i/100ms
         respond_to?   205.432M i/100ms
Calculating -------------------------------------
      begin...rescue     88.510k (± 3.4%) i/s -    442.500k in   5.005408s
         respond_to?      2.021B (± 4.2%) i/s -     10.272B in   5.090954s

Comparison:
         respond_to?: 2021318727.0 i/s
      begin...rescue:    88510.3 i/s - 22837.09x  (± 0.00) slower

$ ruby -v code/general/block-apply-method.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   203.597M i/100ms
             &method   193.323M i/100ms
Calculating -------------------------------------
              normal      2.039B (± 3.7%) i/s -     10.180B in   5.000395s
             &method      2.045B (± 3.3%) i/s -     10.246B in   5.016414s

Comparison:
             &method: 2044810947.0 i/s
              normal: 2038787511.1 i/s - same-ish: difference falls within error

$ ruby -v code/general/define_method-vs-module-eval.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                        21.000  i/100ms
       define_method    51.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.341k (±42.3%) i/s -      3.948k in   5.254626s
       define_method      3.223k (±30.5%) i/s -     11.322k in   6.298795s

Comparison:
       define_method:     3223.2 i/s
module_eval with string:     1341.0 i/s - 2.40x  (± 0.00) slower

$ ruby -v code/general/format-vs-round-and-to-s.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    59.802k i/100ms
       Kernel#format    74.742k i/100ms
            String#%    80.651k i/100ms
Calculating -------------------------------------
         Float#round    601.855k (± 4.2%) i/s -      3.050M in   5.076600s
       Kernel#format    815.942k (± 3.6%) i/s -      4.111M in   5.044789s
            String#%    808.238k (± 3.6%) i/s -      4.113M in   5.095691s

Comparison:
       Kernel#format:   815941.6 i/s
            String#%:   808237.5 i/s - same-ish: difference falls within error
         Float#round:   601855.4 i/s - 1.36x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct-on-access.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   208.254M i/100ms
          OpenStruct    66.988M i/100ms
Calculating -------------------------------------
                Hash      2.050B (± 3.3%) i/s -     10.413B in   5.085518s
          OpenStruct    677.824M (± 3.5%) i/s -      3.416B in   5.046546s

Comparison:
                Hash: 2049771394.7 i/s
          OpenStruct: 677823883.7 i/s - 3.02x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   208.178M i/100ms
          OpenStruct   209.859M i/100ms
Calculating -------------------------------------
                Hash      2.042B (± 3.4%) i/s -     10.201B in   5.002414s
          OpenStruct      2.039B (± 3.5%) i/s -     10.283B in   5.048547s

Comparison:
                Hash: 2041767437.0 i/s
          OpenStruct: 2039431144.3 i/s - same-ish: difference falls within error

$ ruby -v code/general/inheritance-check.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal     1.335M i/100ms
  ancestors.include?   176.497k i/100ms
Calculating -------------------------------------
  less than or equal     13.154M (± 4.5%) i/s -     66.746M in   5.084824s
  ancestors.include?      1.806M (± 4.1%) i/s -      9.178M in   5.091627s

Comparison:
  less than or equal: 13154176.3 i/s
  ancestors.include?:  1805651.8 i/s - 7.29x  (± 0.00) slower

$ ruby -v code/general/loop-vs-while-true.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     1.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     32.550  (± 6.1%) i/s -    163.000  in   5.023692s
         Kernel loop      8.299  (± 0.0%) i/s -     42.000  in   5.066840s

Comparison:
          While Loop:       32.5 i/s
         Kernel loop:        8.3 i/s - 3.92x  (± 0.00) slower

$ ruby -v code/general/raise-vs-e2mmap.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Ruby exception: E2MM#Raise
                       131.000  i/100ms
Ruby exception: Kernel#raise
                       199.038M i/100ms
Calculating -------------------------------------
Ruby exception: E2MM#Raise
                          8.730k (± 7.8%) i/s -     43.361k in   5.001659s
Ruby exception: Kernel#raise
                          2.044B (± 3.9%) i/s -     10.350B in   5.072759s

Comparison:
Ruby exception: Kernel#raise: 2043665156.9 i/s
Ruby exception: E2MM#Raise:     8729.7 i/s - 234104.32x  (± 0.00) slower

Warming up --------------------------------------
Custom exception: E2MM#Raise
                       232.000  i/100ms
Custom exception: Kernel#raise
                       178.974M i/100ms
Calculating -------------------------------------
Custom exception: E2MM#Raise
                          8.868k (± 6.3%) i/s -     44.312k in   5.018357s
Custom exception: Kernel#raise
                          2.036B (± 3.4%) i/s -     10.202B in   5.016377s

Comparison:
Custom exception: Kernel#raise: 2036048575.1 i/s
Custom exception: E2MM#Raise:     8867.7 i/s - 229603.54x  (± 0.00) slower

$ ruby -v code/array/array-first-vs-index.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   199.783M i/100ms
         Array#first   198.277M i/100ms
Calculating -------------------------------------
           Array#[0]      2.052B (± 3.2%) i/s -     10.389B in   5.068132s
         Array#first      2.032B (± 3.1%) i/s -     10.310B in   5.080305s

Comparison:
           Array#[0]: 2052092887.0 i/s
         Array#first: 2031501142.8 i/s - same-ish: difference falls within error

$ ruby -v code/array/array-last-vs-index.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   336.113M i/100ms
          Array#last   317.968M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.262B (± 2.9%) i/s -     16.470B in   5.052981s
          Array#last      3.270B (± 3.7%) i/s -     16.534B in   5.063694s

Comparison:
          Array#last: 3269883093.8 i/s
          Array#[-1]: 3262184030.0 i/s - same-ish: difference falls within error

$ ruby -v code/array/bsearch-vs-find.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   278.521k i/100ms
Calculating -------------------------------------
                find      0.090  (± 0.0%) i/s -      1.000  in  11.087394s
             bsearch      2.782M (± 7.6%) i/s -     13.926M in   5.036568s

Comparison:
             bsearch:  2781840.2 i/s
                find:        0.1 i/s - 30843357.15x  (± 0.00) slower

$ ruby -v code/array/insert-vs-unshift.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.158  (± 0.0%) i/s -      1.000  in   6.326386s
        Array#insert      0.294  (± 0.0%) i/s -      2.000  in   6.802139s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.86x  (± 0.00) slower

$ ruby -v code/array/length-vs-size-vs-count.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   336.020M i/100ms
          Array#size   313.542M i/100ms
         Array#count   326.429M i/100ms
Calculating -------------------------------------
        Array#length      3.170B (± 5.9%) i/s -     15.793B in   5.000195s
          Array#size      3.266B (± 3.3%) i/s -     16.618B in   5.093022s
         Array#count      3.285B (± 3.2%) i/s -     16.648B in   5.073702s

Comparison:
         Array#count: 3284725043.6 i/s
          Array#size: 3266408103.8 i/s - same-ish: difference falls within error
        Array#length: 3169789286.8 i/s - same-ish: difference falls within error

$ ruby -v code/array/shuffle-first-vs-sample.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    13.715k i/100ms
        Array#sample     1.387M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    135.924k (± 7.3%) i/s -    685.750k in   5.086721s
        Array#sample     14.275M (± 2.6%) i/s -     72.113M in   5.055444s

Comparison:
        Array#sample: 14274670.3 i/s
 Array#shuffle.first:   135924.1 i/s - 105.02x  (± 0.00) slower

$ ruby -v code/date/iso8601-vs-parse.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601   233.000  i/100ms
          Date.parse   176.000  i/100ms
Calculating -------------------------------------
        Date.iso8601     33.084k (±32.6%) i/s -     93.899k in   4.998046s
          Date.parse     42.514k (±10.6%) i/s -    209.088k in   4.998583s

Comparison:
          Date.parse:    42514.2 i/s
        Date.iso8601:    33083.6 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/each-push-vs-map.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   282.473k i/100ms
           Array#map   826.053k i/100ms
Calculating -------------------------------------
   Array#each + push      2.847M (± 2.6%) i/s -     14.406M in   5.064200s
           Array#map      8.801M (± 3.0%) i/s -     44.607M in   5.072990s

Comparison:
           Array#map:  8800968.3 i/s
   Array#each + push:  2846596.0 i/s - 3.09x  (± 0.00) slower

$ ruby -v code/enumerable/each-vs-for-loop.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop     1.214M i/100ms
               #each     1.612M i/100ms
Calculating -------------------------------------
            For loop     11.752M (± 3.2%) i/s -     59.509M in   5.069216s
               #each     16.225M (± 3.6%) i/s -     82.224M in   5.074877s

Comparison:
               #each: 16224608.4 i/s
            For loop: 11751803.0 i/s - 1.38x  (± 0.00) slower

$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   358.761k i/100ms
     each_with_index   906.932k i/100ms
Calculating -------------------------------------
          While Loop      3.618M (± 3.1%) i/s -     18.297M in   5.062650s
     each_with_index      9.110M (± 4.0%) i/s -     46.254M in   5.085586s

Comparison:
     each_with_index:  9110457.4 i/s
          While Loop:  3617535.0 i/s - 2.52x  (± 0.00) slower

$ ruby -v code/enumerable/inject-symbol-vs-block.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   136.388k i/100ms
      inject to_proc   129.971k i/100ms
        inject block   134.193k i/100ms
Calculating -------------------------------------
       inject symbol      1.352M (± 3.8%) i/s -      6.819M in   5.050882s
      inject to_proc      1.359M (± 2.4%) i/s -      6.888M in   5.070709s
        inject block      1.336M (± 3.6%) i/s -      6.710M in   5.027936s

Comparison:
      inject to_proc:  1359299.7 i/s
       inject symbol:  1352245.1 i/s - same-ish: difference falls within error
        inject block:  1336255.3 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    26.265k i/100ms
   Array#map.flatten    11.929k i/100ms
      Array#flat_map    55.944k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    263.149k (± 4.3%) i/s -      1.313M in   5.000248s
   Array#map.flatten    155.878k (± 5.6%) i/s -    787.314k in   5.068194s
      Array#flat_map    566.018k (± 3.5%) i/s -      2.853M in   5.047234s

Comparison:
      Array#flat_map:   566017.7 i/s
Array#map.flatten(1):   263149.3 i/s - 2.15x  (± 0.00) slower
   Array#map.flatten:   155878.5 i/s - 3.63x  (± 0.00) slower

$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   201.445k i/100ms
  Array#reverse_each   471.847k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.125M (± 3.1%) i/s -     10.677M in   5.028500s
  Array#reverse_each      4.833M (± 3.7%) i/s -     24.536M in   5.083580s

Comparison:
  Array#reverse_each:  4833470.5 i/s
  Array#reverse.each:  2125295.9 i/s - 2.27x  (± 0.00) slower

$ ruby -v code/enumerable/select-first-vs-detect.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       636.089k i/100ms
   Enumerable#detect     4.599M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          6.340M (± 3.0%) i/s -    127.218M in  20.085396s
   Enumerable#detect     46.606M (± 3.7%) i/s -    933.577M in  20.059533s

Comparison:
   Enumerable#detect: 46606019.4 i/s
Enumerable#select.first:  6339725.0 i/s - 7.35x  (± 0.00) slower

$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       198.140k i/100ms
Enumerable#select.last
                       415.778k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.072M (± 3.5%) i/s -     10.501M in   5.074550s
Enumerable#select.last
                          4.115M (± 3.9%) i/s -     20.789M in   5.060286s

Comparison:
Enumerable#select.last:  4114837.2 i/s
Enumerable#reverse.detect:  2072116.4 i/s - 1.99x  (± 0.00) slower

$ ruby -v code/enumerable/sort-vs-sort_by.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         2.136k i/100ms
  Enumerable#sort_by     4.123k i/100ms
     Enumerable#sort     6.504k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         56.758k (±18.2%) i/s -    239.232k in   5.017290s
  Enumerable#sort_by     54.453k (±17.4%) i/s -    243.257k in   5.019826s
     Enumerable#sort     68.940k (± 3.3%) i/s -    344.712k in   5.005773s

Comparison:
     Enumerable#sort:    68940.3 i/s
Enumerable#sort_by (Symbol#to_proc):    56757.6 i/s - same-ish: difference falls within error
  Enumerable#sort_by:    54453.4 i/s - 1.27x  (± 0.00) slower

$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   323.639k i/100ms
Enumerable#sort_by...first
                         9.858k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      3.280M (± 3.3%) i/s -     16.506M in   5.038164s
Enumerable#sort_by...first
                        102.935k (± 3.6%) i/s -    522.474k in   5.082453s

Comparison:
   Enumerable#min_by:  3279843.5 i/s
Enumerable#sort_by...first:   102935.4 i/s - 31.86x  (± 0.00) slower

$ ruby -v code/hash/bracket-vs-dup.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   553.531k i/100ms
            Hash#dup   576.840k i/100ms
Calculating -------------------------------------
              Hash[]      5.694M (± 4.3%) i/s -     28.784M in   5.064910s
            Hash#dup      5.605M (± 8.8%) i/s -     27.688M in   5.013671s

Comparison:
              Hash[]:  5693851.2 i/s
            Hash#dup:  5605332.1 i/s - same-ish: difference falls within error

$ ruby -v code/hash/bracket-vs-fetch.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   334.831M i/100ms
  Hash#fetch, symbol   207.563M i/100ms
     Hash#[], string     8.810M i/100ms
  Hash#fetch, string     8.507M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      3.279B (± 3.5%) i/s -     16.407B in   5.010095s
  Hash#fetch, symbol      2.042B (± 3.6%) i/s -     10.378B in   5.089212s
     Hash#[], string     88.805M (± 3.3%) i/s -    449.315M in   5.065350s
  Hash#fetch, string     85.456M (± 3.4%) i/s -    433.835M in   5.082825s

Comparison:
     Hash#[], symbol: 3278999587.9 i/s
  Hash#fetch, symbol: 2041950585.3 i/s - 1.61x  (± 0.00) slower
     Hash#[], string: 88804926.3 i/s - 36.92x  (± 0.00) slower
  Hash#fetch, string: 85455991.4 i/s - 38.37x  (± 0.00) slower

$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig   318.015k i/100ms
             Hash#[]     5.257M i/100ms
          Hash#[] ||     5.303M i/100ms
          Hash#[] &&     5.194M i/100ms
          Hash#fetch     4.695M i/100ms
 Hash#fetch fallback     4.953M i/100ms
Calculating -------------------------------------
            Hash#dig      9.371M (± 5.4%) i/s -     46.748M in   5.003739s
             Hash#[]     51.668M (± 3.6%) i/s -    262.833M in   5.093763s
          Hash#[] ||     51.656M (± 4.1%) i/s -    259.835M in   5.039376s
          Hash#[] &&     51.632M (± 3.2%) i/s -    259.711M in   5.035323s
          Hash#fetch     49.225M (± 3.5%) i/s -    248.829M in   5.061245s
 Hash#fetch fallback     49.456M (± 2.9%) i/s -    247.630M in   5.011588s

Comparison:
             Hash#[]: 51668221.5 i/s
          Hash#[] ||: 51655925.9 i/s - same-ish: difference falls within error
          Hash#[] &&: 51632371.4 i/s - same-ish: difference falls within error
 Hash#fetch fallback: 49455574.8 i/s - same-ish: difference falls within error
          Hash#fetch: 49225133.7 i/s - same-ish: difference falls within error
            Hash#dig:  9371010.9 i/s - 5.51x  (± 0.00) slower

$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   330.531M i/100ms
  Hash#fetch + block   191.743M i/100ms
    Hash#fetch + arg   324.767M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      3.281B (± 4.4%) i/s -     16.527B in   5.047704s
  Hash#fetch + block      2.039B (± 3.7%) i/s -     10.354B in   5.084362s
    Hash#fetch + arg      3.296B (± 2.9%) i/s -     16.563B in   5.030406s

Comparison:
    Hash#fetch + arg: 3295540210.9 i/s
  Hash#fetch + const: 3281220143.4 i/s - same-ish: difference falls within error
  Hash#fetch + block: 2039417201.7 i/s - 1.62x  (± 0.00) slower

$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h     2.402k i/100ms
         sort + to_h     1.560k i/100ms
Calculating -------------------------------------
      sort_by + to_h    507.619k (±29.1%) i/s -      2.186M in   4.996036s
         sort + to_h     82.654k (± 6.0%) i/s -    411.840k in   5.002350s

Comparison:
      sort_by + to_h:   507618.9 i/s
         sort + to_h:    82653.8 i/s - 6.14x  (± 0.00) slower

$ ruby -v code/hash/keys-each-vs-each_key.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each   298.940k i/100ms
       Hash#each_key   341.303k i/100ms
Calculating -------------------------------------
      Hash#keys.each      2.862M (± 3.7%) i/s -     14.349M in   5.020963s
       Hash#each_key      3.408M (± 2.9%) i/s -     17.065M in   5.012269s

Comparison:
       Hash#each_key:  3407697.4 i/s
      Hash#keys.each:  2861878.9 i/s - 1.19x  (± 0.00) slower

$ ruby -v code/hash/keys-include-vs-key.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?    69.000  i/100ms
           Hash#key?     5.787M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      3.857k (±11.6%) i/s -     18.906k in   4.998172s
           Hash#key?     60.885M (± 4.3%) i/s -    306.687M in   5.047081s

Comparison:
           Hash#key?: 60884658.2 i/s
  Hash#keys.include?:     3857.3 i/s - 15784.19x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-[]=.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    15.877k i/100ms
            Hash#[]=    48.276k i/100ms
Calculating -------------------------------------
         Hash#merge!    503.163k (± 5.8%) i/s -      2.509M in   5.004059s
            Hash#[]=    515.179k (± 4.0%) i/s -      2.607M in   5.068603s

Comparison:
            Hash#[]=:   515179.2 i/s
         Hash#merge!:   503162.7 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                         1.646k i/100ms
      Hash#merge({})    16.224k i/100ms
 Hash#dup#merge!({})    26.290k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        264.287k (±11.2%) i/s -      1.300M in   4.993239s
      Hash#merge({})    162.149k (± 3.7%) i/s -    811.200k in   5.010298s
 Hash#dup#merge!({})    264.992k (± 8.9%) i/s -      1.315M in   5.042471s

Comparison:
 Hash#dup#merge!({}):   264991.6 i/s
{}#merge!(Hash) do end:   264287.3 i/s - same-ish: difference falls within error
      Hash#merge({}):   162148.8 i/s - 1.63x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-double-splat-operator.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   200.411M i/100ms
          Hash#merge   201.626M i/100ms
Calculating -------------------------------------
        Hash#**other      2.056B (± 3.7%) i/s -     10.421B in   5.075549s
          Hash#merge      2.048B (± 4.0%) i/s -     10.283B in   5.029475s

Comparison:
        Hash#**other: 2056241162.5 i/s
          Hash#merge: 2048083185.2 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-vs-merge-bang.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge   225.000  i/100ms
         Hash#merge!    51.932k i/100ms
Calculating -------------------------------------
          Hash#merge      8.970k (± 6.1%) i/s -     44.775k in   5.011791s
         Hash#merge!    509.338k (± 3.4%) i/s -      2.545M in   5.001805s

Comparison:
         Hash#merge!:   509338.2 i/s
          Hash#merge:     8969.8 i/s - 56.78x  (± 0.00) slower

$ ruby -v code/hash/slice-native-vs-before-native.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice        1.976M i/100ms
Array#each               1.499M i/100ms
Array#each_w/_object     1.483M i/100ms
Hash#select-include      2.366M i/100ms
Calculating -------------------------------------
Hash#native-slice        19.543M (± 3.0%) i/s -     98.780M in   5.059153s
Array#each               14.836M (± 2.9%) i/s -     74.940M in   5.055700s
Array#each_w/_object     14.836M (± 3.2%) i/s -     74.130M in   5.001950s
Hash#select-include      23.849M (± 4.4%) i/s -    120.645M in   5.068856s

Comparison:
Hash#select-include : 23849409.5 i/s
Hash#native-slice   : 19543441.4 i/s - 1.22x  (± 0.00) slower
Array#each          : 14836012.4 i/s - 1.61x  (± 0.00) slower
Array#each_w/_object: 14836005.1 i/s - 1.61x  (± 0.00) slower

$ ruby -v code/hash/values-include-vs-value.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?    90.000  i/100ms
         Hash#value?     3.103k i/100ms
Calculating -------------------------------------
Hash#values.include?      4.073k (±12.7%) i/s -     19.980k in   5.009874s
         Hash#value?     30.558k (± 3.6%) i/s -    155.150k in   5.084073s

Comparison:
         Hash#value?:    30558.1 i/s
Hash#values.include?:     4072.8 i/s - 7.50x  (± 0.00) slower

$ ruby -v code/method/call-vs-send-vs-method_missing.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   198.182M i/100ms
                send   205.653M i/100ms
      method_missing   208.532M i/100ms
Calculating -------------------------------------
                call      2.056B (± 3.7%) i/s -     10.305B in   5.019619s
                send      2.059B (± 3.2%) i/s -     10.488B in   5.098787s
      method_missing      2.033B (± 4.0%) i/s -     10.218B in   5.033441s

Comparison:
                send: 2059117543.5 i/s
                call: 2055854490.7 i/s - same-ish: difference falls within error
      method_missing: 2033478259.8 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/block-vs-to_proc.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    60.623k i/100ms
      Symbol#to_proc    60.084k i/100ms
Calculating -------------------------------------
               Block    603.280k (± 8.6%) i/s -      3.031M in   5.100442s
      Symbol#to_proc    588.197k (± 9.1%) i/s -      2.944M in   5.085941s

Comparison:
               Block:   603279.7 i/s
      Symbol#to_proc:   588197.3 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   327.980M i/100ms
       block + yield   320.238M i/100ms
        unused block   332.594M i/100ms
               yield   330.740M i/100ms
Calculating -------------------------------------
          block.call      3.293B (± 2.9%) i/s -     16.727B in   5.083805s
       block + yield      3.287B (± 3.2%) i/s -     16.652B in   5.070969s
        unused block      3.295B (± 3.4%) i/s -     16.630B in   5.052749s
               yield      3.273B (± 3.2%) i/s -     16.537B in   5.057692s

Comparison:
        unused block: 3295137088.6 i/s
          block.call: 3293019827.5 i/s - same-ish: difference falls within error
       block + yield: 3287247012.7 i/s - same-ish: difference falls within error
               yield: 3273218903.7 i/s - same-ish: difference falls within error

$ ruby -v code/range/cover-vs-include.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?     6.028M i/100ms
      range#include?     1.789k i/100ms
       range#member?     5.895k i/100ms
       plain compare     7.264M i/100ms
Calculating -------------------------------------
        range#cover?     49.751M (± 9.9%) i/s -    247.129M in   5.066099s
      range#include?     89.764k (± 5.9%) i/s -    447.250k in   5.001917s
       range#member?     92.270k (± 4.3%) i/s -    465.705k in   5.056769s
       plain compare     72.486M (± 3.8%) i/s -    363.219M in   5.018362s

Comparison:
       plain compare: 72486175.9 i/s
        range#cover?: 49751002.4 i/s - 1.46x  (± 0.00) slower
       range#member?:    92269.9 i/s - 785.59x  (± 0.00) slower
      range#include?:    89763.7 i/s - 807.52x  (± 0.00) slower

$ ruby -v code/string/===-vs-=~-vs-match.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     1.585M i/100ms
           String#=~     1.467M i/100ms
          Regexp#===     1.385M i/100ms
        String#match     1.211M i/100ms
Calculating -------------------------------------
       String#match?     15.744M (± 4.4%) i/s -     79.235M in   5.043029s
           String#=~     14.261M (± 3.9%) i/s -     71.878M in   5.048183s
          Regexp#===     14.075M (± 4.0%) i/s -     70.641M in   5.027294s
        String#match     12.277M (± 3.2%) i/s -     61.758M in   5.035528s

Comparison:
       String#match?: 15743594.7 i/s
           String#=~: 14261179.2 i/s - 1.10x  (± 0.00) slower
          Regexp#===: 14075291.2 i/s - 1.12x  (± 0.00) slower
        String#match: 12277206.2 i/s - 1.28x  (± 0.00) slower

$ ruby -v code/string/casecmp-vs-downcase-==.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.367M i/100ms
      String#casecmp     4.565M i/100ms
Calculating -------------------------------------
String#downcase + ==     23.520M (± 3.3%) i/s -    118.359M in   5.037827s
      String#casecmp     44.932M (± 3.0%) i/s -    228.237M in   5.084229s

Comparison:
      String#casecmp: 44932031.8 i/s
String#downcase + ==: 23520305.5 i/s - 1.91x  (± 0.00) slower

$ ruby -v code/string/concatenation.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   204.324M i/100ms
       String#concat   204.281M i/100ms
       String#append   200.066M i/100ms
         "foo" "bar"   196.569M i/100ms
  "#{'foo'}#{'bar'}"   202.916M i/100ms
Calculating -------------------------------------
            String#+      2.038B (± 3.8%) i/s -     10.216B in   5.020802s
       String#concat      2.049B (± 3.4%) i/s -     10.418B in   5.091540s
       String#append      2.057B (± 3.0%) i/s -     10.403B in   5.061752s
         "foo" "bar"      2.057B (± 3.2%) i/s -     10.418B in   5.070026s
  "#{'foo'}#{'bar'}"      2.046B (± 3.7%) i/s -     10.349B in   5.066345s

Comparison:
       String#append: 2057204956.3 i/s
         "foo" "bar": 2057013978.2 i/s - same-ish: difference falls within error
       String#concat: 2048607704.0 i/s - same-ish: difference falls within error
  "#{'foo'}#{'bar'}": 2045582377.7 i/s - same-ish: difference falls within error
            String#+: 2037783172.6 i/s - same-ish: difference falls within error

$ ruby -v code/string/dup-vs-unary-plus.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   328.628M i/100ms
          String#dup   208.856M i/100ms
Calculating -------------------------------------
           String#+@      3.297B (± 2.9%) i/s -     16.760B in   5.088486s
          String#dup      2.054B (± 3.3%) i/s -     10.443B in   5.089570s

Comparison:
           String#+@: 3296572339.9 i/s
          String#dup: 2054127589.7 i/s - 1.60x  (± 0.00) slower

$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   227.064k i/100ms
       String#match?   228.611k i/100ms
    String#end_with?   983.507k i/100ms
Calculating -------------------------------------
           String#=~      2.210M (± 3.6%) i/s -     11.126M in   5.041073s
       String#match?      2.369M (± 3.5%) i/s -     11.888M in   5.025154s
    String#end_with?      9.589M (± 4.2%) i/s -     48.192M in   5.034830s

Comparison:
    String#end_with?:  9589470.3 i/s
       String#match?:  2368708.6 i/s - 4.05x  (± 0.00) slower
           String#=~:  2210073.4 i/s - 4.34x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-sub.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    26.719k i/100ms
          String#sub    92.408k i/100ms
String#dup["string"]=
                         6.050M i/100ms
Calculating -------------------------------------
         String#gsub    938.394k (± 4.8%) i/s -      4.703M in   5.023433s
          String#sub    882.701k (± 3.8%) i/s -      4.436M in   5.032496s
String#dup["string"]=
                         60.635M (± 3.5%) i/s -    308.565M in   5.095183s

Comparison:
String#dup["string"]=: 60634894.8 i/s
         String#gsub:   938394.1 i/s - 64.62x  (± 0.00) slower
          String#sub:   882701.4 i/s - 68.69x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-tr.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    48.587k i/100ms
           String#tr   280.339k i/100ms
Calculating -------------------------------------
         String#gsub      2.957M (± 7.1%) i/s -     14.722M in   5.006868s
           String#tr      2.783M (± 3.0%) i/s -     14.017M in   5.040431s

Comparison:
         String#gsub:  2957075.4 i/s
           String#tr:  2783343.6 i/s - same-ish: difference falls within error

$ ruby -v code/string/mutable_vs_immutable_strings.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze   208.001M i/100ms
         With Freeze   198.148M i/100ms
Calculating -------------------------------------
      Without Freeze      2.062B (± 2.9%) i/s -     10.400B in   5.047239s
         With Freeze      2.045B (± 3.9%) i/s -     10.304B in   5.046014s

Comparison:
      Without Freeze: 2062299108.2 i/s
         With Freeze: 2045109078.7 i/s - same-ish: difference falls within error

$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/   557.000  i/100ms
      String#squeeze    60.552k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     38.102k (± 7.0%) i/s -    189.380k in   4.997610s
      String#squeeze    594.055k (± 3.8%) i/s -      2.967M in   5.001964s

Comparison:
      String#squeeze:   594054.6 i/s
 String#gsub/regex+/:    38101.6 i/s - 15.59x  (± 0.00) slower

$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   676.705k i/100ms
       String#match?   993.275k i/100ms
  String#start_with?     2.983M i/100ms
Calculating -------------------------------------
           String#=~      7.156M (± 3.2%) i/s -     35.865M in   5.016937s
       String#match?      9.798M (± 3.0%) i/s -     49.664M in   5.073187s
  String#start_with?     28.906M (± 3.9%) i/s -    146.184M in   5.065265s

Comparison:
  String#start_with?: 28906444.3 i/s
       String#match?:  9798275.2 i/s - 2.95x  (± 0.00) slower
           String#=~:  7156435.0 i/s - 4.04x  (± 0.00) slower

$ ruby -v code/string/start_with-vs-substring-==.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?   581.260k i/100ms
    String#[0, n] ==   482.814k i/100ms
   String#[RANGE] ==   492.018k i/100ms
   String#[0...n] ==   358.264k i/100ms
Calculating -------------------------------------
  String#start_with?      5.808M (± 3.6%) i/s -     29.063M in   5.011054s
    String#[0, n] ==      4.721M (± 6.0%) i/s -     23.658M in   5.036216s
   String#[RANGE] ==      4.917M (± 4.5%) i/s -     24.601M in   5.014204s
   String#[0...n] ==      3.761M (± 3.6%) i/s -     18.988M in   5.055472s

Comparison:
  String#start_with?:  5807682.9 i/s
   String#[RANGE] ==:  4916876.8 i/s - 1.18x  (± 0.00) slower
    String#[0, n] ==:  4721456.7 i/s - 1.23x  (± 0.00) slower
   String#[0...n] ==:  3761035.8 i/s - 1.54x  (± 0.00) slower

$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=     6.278M i/100ms
 String#sub!'string'    92.073k i/100ms
String#gsub!'string'    67.497k i/100ms
  String#[/regexp/]=   432.346k i/100ms
 String#sub!/regexp/   696.498k i/100ms
String#gsub!/regexp/    98.473k i/100ms
Calculating -------------------------------------
  String#['string']=     60.115M (± 4.2%) i/s -    301.356M in   5.022626s
 String#sub!'string'    908.197k (± 3.6%) i/s -      4.604M in   5.075839s
String#gsub!'string'    921.810k (± 4.5%) i/s -      4.657M in   5.063307s
  String#[/regexp/]=      4.315M (± 4.0%) i/s -     21.617M in   5.017871s
 String#sub!/regexp/      6.989M (± 4.6%) i/s -     35.521M in   5.094003s
String#gsub!/regexp/      2.743M (± 5.8%) i/s -     13.688M in   5.008278s

Comparison:
  String#['string']=: 60115360.3 i/s
 String#sub!/regexp/:  6988995.7 i/s - 8.60x  (± 0.00) slower
  String#[/regexp/]=:  4315165.3 i/s - 13.93x  (± 0.00) slower
String#gsub!/regexp/:  2743062.5 i/s - 21.92x  (± 0.00) slower
String#gsub!'string':   921810.5 i/s - 65.21x  (± 0.00) slower
 String#sub!'string':   908196.7 i/s - 66.19x  (± 0.00) slower

$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub   588.892k i/100ms
        String#chomp     2.269M i/100ms
String#delete_suffix     2.093M i/100ms
Calculating -------------------------------------
          String#sub      5.984M (± 3.3%) i/s -     30.033M in   5.024450s
        String#chomp     22.161M (± 4.3%) i/s -    111.179M in   5.026376s
String#delete_suffix     21.842M (± 4.2%) i/s -    110.910M in   5.087468s

Comparison:
        String#chomp: 22160748.0 i/s
String#delete_suffix: 21842084.5 i/s - same-ish: difference falls within error
          String#sub:  5984080.9 i/s - 3.70x  (± 0.00) slower

$ ruby -v code/string/sub-vs-delete_prefix.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     2.465M i/100ms
          String#sub   699.714k i/100ms
Calculating -------------------------------------
String#delete_prefix     26.007M (± 4.0%) i/s -    130.660M in   5.032628s
          String#sub      6.861M (± 3.4%) i/s -     34.286M in   5.002825s

Comparison:
String#delete_prefix: 26006742.4 i/s
          String#sub:  6861335.9 i/s - 3.79x  (± 0.00) slower

$ ruby -v code/string/unpack1-vs-unpack[0].rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     2.313M i/100ms
    String#unpack[0]     2.318M i/100ms
Calculating -------------------------------------
      String#unpack1     22.831M (± 4.1%) i/s -    115.646M in   5.074310s
    String#unpack[0]     22.803M (± 3.9%) i/s -    115.912M in   5.091178s

Comparison:
      String#unpack1: 22830688.5 i/s
    String#unpack[0]: 22803101.2 i/s - same-ish: difference falls within error

$ ruby -v code/time/iso8601-vs-parse.rb
truffleruby 20.3.0-dev-d1ce9c0d, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601   846.000  i/100ms
          Time.parse   238.000  i/100ms
Calculating -------------------------------------
        Time.iso8601    288.306k (±19.5%) i/s -      1.193M in   4.993787s
          Time.parse     41.996k (± 9.3%) i/s -    207.536k in   4.999632s

Comparison:
        Time.iso8601:   288305.8 i/s
          Time.parse:    41996.0 i/s - 6.87x  (± 0.00) slower




$ ruby -v code/general/array-argument-vs-splat-arguments.rb
$ ruby -v code/general/assignment.rb
$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
$ ruby -v code/general/begin-rescue-vs-respond-to.rb
$ ruby -v code/general/block-apply-method.rb
$ ruby -v code/general/define_method-vs-module-eval.rb
$ ruby -v code/general/format-vs-round-and-to-s.rb
$ ruby -v code/general/hash-vs-openstruct-on-access.rb
$ ruby -v code/general/hash-vs-openstruct.rb
$ ruby -v code/general/inheritance-check.rb
$ ruby -v code/general/loop-vs-while-true.rb
$ ruby -v code/general/raise-vs-e2mmap.rb
$ ruby -v code/array/array-first-vs-index.rb
$ ruby -v code/array/array-last-vs-index.rb
$ ruby -v code/array/bsearch-vs-find.rb
$ ruby -v code/array/insert-vs-unshift.rb
$ ruby -v code/array/length-vs-size-vs-count.rb
$ ruby -v code/array/shuffle-first-vs-sample.rb
$ ruby -v code/date/iso8601-vs-parse.rb
$ ruby -v code/enumerable/each-push-vs-map.rb
$ ruby -v code/enumerable/each-vs-for-loop.rb
$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
$ ruby -v code/enumerable/inject-symbol-vs-block.rb
$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
$ ruby -v code/enumerable/select-first-vs-detect.rb
$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
$ ruby -v code/enumerable/sort-vs-sort_by.rb
$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
$ ruby -v code/hash/bracket-vs-dup.rb
$ ruby -v code/hash/bracket-vs-fetch.rb
$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
$ ruby -v code/hash/keys-each-vs-each_key.rb
$ ruby -v code/hash/keys-include-vs-key.rb
$ ruby -v code/hash/merge-bang-vs-[]=.rb
$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
$ ruby -v code/hash/merge-vs-double-splat-operator.rb
$ ruby -v code/hash/merge-vs-merge-bang.rb
$ ruby -v code/hash/slice-native-vs-before-native.rb
$ ruby -v code/hash/values-include-vs-value.rb
$ ruby -v code/method/call-vs-send-vs-method_missing.rb
$ ruby -v code/proc-and-block/block-vs-to_proc.rb
$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
$ ruby -v code/range/cover-vs-include.rb
$ ruby -v code/string/===-vs-=~-vs-match.rb
$ ruby -v code/string/casecmp-vs-downcase-==.rb
$ ruby -v code/string/concatenation.rb
$ ruby -v code/string/dup-vs-unary-plus.rb
$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
$ ruby -v code/string/gsub-vs-sub.rb
$ ruby -v code/string/gsub-vs-tr.rb
$ ruby -v code/string/mutable_vs_immutable_strings.rb
$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
$ ruby -v code/string/start_with-vs-substring-==.rb
$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
$ ruby -v code/string/sub-vs-delete_prefix.rb
$ ruby -v code/string/unpack1-vs-unpack[0].rb
$ ruby -v code/time/iso8601-vs-parse.rb
```



## License

![CC-BY-SA](CC-BY-SA.png)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Code License

### CC0 1.0 Universal

To the extent possible under law, @JuanitoFatas has waived all copyright and related or neighboring rights to "fast-ruby".

This work belongs to the community.
