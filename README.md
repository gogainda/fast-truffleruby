## Fast Truffle Ruby 


The idia of this project is to run all collected examples from the [Fast Ruby] (https://github.com/JuanitoFatas/fast-ruby) and run it against the latest truffle ruby version to see if the same results hold for the Truffle ruby. 

As you will see in the resalst below some results a quite different

## Results
```
$ ruby -v code/general/array-argument-vs-splat-arguments.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       205.974M i/100ms
Function with splat arguments
                         1.493k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          2.137B (± 2.5%) i/s -     10.711B in   5.015649s
Function with splat arguments
                         14.543k (± 6.9%) i/s -     74.650k in   5.171246s

Comparison:
Function with single Array argument: 2136861148.0 i/s
Function with splat arguments:    14543.4 i/s - 146930.21x  (± 0.00) slower

$ ruby -v code/general/assignment.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   216.604M i/100ms
Sequential Assignment
                       218.729M i/100ms
Calculating -------------------------------------
 Parallel Assignment      2.107B (± 4.9%) i/s -     10.614B in   5.051265s
Sequential Assignment
                          2.137B (± 2.3%) i/s -     10.718B in   5.018327s

Comparison:
Sequential Assignment: 2136827120.4 i/s
 Parallel Assignment: 2106599751.1 i/s - same-ish: difference falls within error

$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   193.807M i/100ms
       attr_accessor   212.820M i/100ms
Calculating -------------------------------------
   getter_and_setter      2.134B (± 3.0%) i/s -     10.659B in   5.000604s
       attr_accessor      2.143B (± 2.7%) i/s -     10.854B in   5.068550s

Comparison:
       attr_accessor: 2143059372.7 i/s
   getter_and_setter: 2133554854.8 i/s - same-ish: difference falls within error

$ ruby -v code/general/begin-rescue-vs-respond-to.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     8.581k i/100ms
         respond_to?   215.996M i/100ms
Calculating -------------------------------------
      begin...rescue     87.424k (± 2.0%) i/s -    437.631k in   5.007826s
         respond_to?      2.141B (± 2.3%) i/s -     10.800B in   5.046037s

Comparison:
         respond_to?: 2141414080.5 i/s
      begin...rescue:    87424.1 i/s - 24494.54x  (± 0.00) slower

$ ruby -v code/general/block-apply-method.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   213.882M i/100ms
             &method   217.040M i/100ms
Calculating -------------------------------------
              normal      2.130B (± 3.0%) i/s -     10.694B in   5.025287s
             &method      2.134B (± 2.2%) i/s -     10.852B in   5.087358s

Comparison:
             &method: 2134227225.3 i/s
              normal: 2130092922.9 i/s - same-ish: difference falls within error

$ ruby -v code/general/define_method-vs-module-eval.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                        50.000  i/100ms
       define_method   233.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.167k (±33.1%) i/s -      5.100k in   5.006923s
       define_method      2.706k (±37.5%) i/s -      8.854k in   5.101022s

Comparison:
       define_method:     2706.5 i/s
module_eval with string:     1167.0 i/s - 2.32x  (± 0.00) slower

$ ruby -v code/general/format-vs-round-and-to-s.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    61.431k i/100ms
       Kernel#format    84.159k i/100ms
            String#%    83.626k i/100ms
Calculating -------------------------------------
         Float#round    623.206k (± 2.4%) i/s -      3.133M in   5.030153s
       Kernel#format    841.401k (± 1.7%) i/s -      4.208M in   5.002599s
            String#%    830.345k (± 2.6%) i/s -      4.181M in   5.039094s

Comparison:
       Kernel#format:   841401.3 i/s
            String#%:   830344.9 i/s - same-ish: difference falls within error
         Float#round:   623205.5 i/s - 1.35x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct-on-access.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   335.468M i/100ms
          OpenStruct    71.044M i/100ms
Calculating -------------------------------------
                Hash      3.422B (± 2.1%) i/s -     17.109B in   5.002276s
          OpenStruct    712.359M (± 2.4%) i/s -      3.623B in   5.089415s

Comparison:
                Hash: 3421775296.8 i/s
          OpenStruct: 712359464.9 i/s - 4.80x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   200.614M i/100ms
          OpenStruct   212.959M i/100ms
Calculating -------------------------------------
                Hash      2.121B (± 3.4%) i/s -     10.633B in   5.019945s
          OpenStruct      2.106B (± 4.5%) i/s -     10.648B in   5.066792s

Comparison:
                Hash: 2120687218.9 i/s
          OpenStruct: 2106191934.0 i/s - same-ish: difference falls within error

$ ruby -v code/general/inheritance-check.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal     1.112M i/100ms
  ancestors.include?   186.019k i/100ms
Calculating -------------------------------------
  less than or equal     13.511M (± 2.6%) i/s -     67.860M in   5.026167s
  ancestors.include?      1.868M (± 2.1%) i/s -      9.487M in   5.080458s

Comparison:
  less than or equal: 13510684.1 i/s
  ancestors.include?:  1868169.9 i/s - 7.23x  (± 0.00) slower

$ ruby -v code/general/loop-vs-while-true.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     1.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     34.384  (± 2.9%) i/s -    172.000  in   5.008276s
         Kernel loop      8.771  (± 0.0%) i/s -     44.000  in   5.020189s

Comparison:
          While Loop:       34.4 i/s
         Kernel loop:        8.8 i/s - 3.92x  (± 0.00) slower

$ ruby -v code/general/raise-vs-e2mmap.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Ruby exception: E2MM#Raise
                       391.000  i/100ms
Ruby exception: Kernel#raise
                       217.179M i/100ms
Calculating -------------------------------------
Ruby exception: E2MM#Raise
                          7.679k (±19.1%) i/s -     37.145k in   5.043923s
Ruby exception: Kernel#raise
                          2.139B (± 2.3%) i/s -     10.859B in   5.080612s

Comparison:
Ruby exception: Kernel#raise: 2138520313.2 i/s
Ruby exception: E2MM#Raise:     7678.8 i/s - 278494.98x  (± 0.00) slower

Warming up --------------------------------------
Custom exception: E2MM#Raise
                       551.000  i/100ms
Custom exception: Kernel#raise
                       210.356M i/100ms
Calculating -------------------------------------
Custom exception: E2MM#Raise
                          9.172k (± 4.2%) i/s -     46.284k in   5.055720s
Custom exception: Kernel#raise
                          2.091B (± 4.8%) i/s -     10.518B in   5.043527s

Comparison:
Custom exception: Kernel#raise: 2090588478.3 i/s
Custom exception: E2MM#Raise:     9172.1 i/s - 227930.18x  (± 0.00) slower

$ ruby -v code/array/array-first-vs-index.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   214.544M i/100ms
         Array#first   217.757M i/100ms
Calculating -------------------------------------
           Array#[0]      2.149B (± 2.2%) i/s -     10.942B in   5.093189s
         Array#first      2.138B (± 3.0%) i/s -     10.888B in   5.096343s

Comparison:
           Array#[0]: 2149375089.5 i/s
         Array#first: 2138487084.6 i/s - same-ish: difference falls within error

$ ruby -v code/array/array-last-vs-index.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   343.732M i/100ms
          Array#last   345.142M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.434B (± 1.9%) i/s -     17.187B in   5.006756s
          Array#last      3.389B (± 3.4%) i/s -     17.257B in   5.097682s

Comparison:
          Array#[-1]: 3433869503.4 i/s
          Array#last: 3389493085.0 i/s - same-ish: difference falls within error

$ ruby -v code/array/bsearch-vs-find.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   338.860k i/100ms
Calculating -------------------------------------
                find      0.102  (± 0.0%) i/s -      1.000  in   9.817354s
             bsearch      3.328M (±10.2%) i/s -     16.604M in   5.069385s

Comparison:
             bsearch:  3328476.6 i/s
                find:        0.1 i/s - 32676832.36x  (± 0.00) slower

$ ruby -v code/array/insert-vs-unshift.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.167  (± 0.0%) i/s -      1.000  in   5.978233s
        Array#insert      0.309  (± 0.0%) i/s -      2.000  in   6.470406s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.85x  (± 0.00) slower

$ ruby -v code/array/length-vs-size-vs-count.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   335.452M i/100ms
          Array#size   345.236M i/100ms
         Array#count   348.756M i/100ms
Calculating -------------------------------------
        Array#length      3.437B (± 2.5%) i/s -     17.443B in   5.078876s
          Array#size      3.452B (± 2.3%) i/s -     17.262B in   5.003825s
         Array#count      3.435B (± 2.3%) i/s -     17.438B in   5.080048s

Comparison:
          Array#size: 3451649085.9 i/s
        Array#length: 3436680938.9 i/s - same-ish: difference falls within error
         Array#count: 3434513115.6 i/s - same-ish: difference falls within error

$ ruby -v code/array/shuffle-first-vs-sample.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    14.401k i/100ms
        Array#sample     1.495M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    134.723k (± 8.1%) i/s -    676.847k in   5.075590s
        Array#sample     14.781M (± 4.8%) i/s -     74.734M in   5.068350s

Comparison:
        Array#sample: 14780951.3 i/s
 Array#shuffle.first:   134722.6 i/s - 109.71x  (± 0.00) slower

$ ruby -v code/date/iso8601-vs-parse.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601   377.000  i/100ms
          Date.parse   709.000  i/100ms
Calculating -------------------------------------
        Date.iso8601     40.689k (± 9.4%) i/s -    200.941k in   5.000153s
          Date.parse     44.829k (± 5.0%) i/s -    224.044k in   5.011157s

Comparison:
          Date.parse:    44828.9 i/s
        Date.iso8601:    40689.3 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/each-push-vs-map.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   247.503k i/100ms
           Array#map     1.350M i/100ms
Calculating -------------------------------------
   Array#each + push      2.500M (± 2.4%) i/s -     12.623M in   5.052854s
           Array#map     13.519M (± 2.0%) i/s -     68.864M in   5.096073s

Comparison:
           Array#map: 13518760.3 i/s
   Array#each + push:  2499596.6 i/s - 5.41x  (± 0.00) slower

$ ruby -v code/enumerable/each-vs-for-loop.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop     1.245M i/100ms
               #each     1.700M i/100ms
Calculating -------------------------------------
            For loop     12.411M (± 2.3%) i/s -     62.245M in   5.017816s
               #each     16.896M (± 3.0%) i/s -     85.019M in   5.036579s

Comparison:
               #each: 16896113.7 i/s
            For loop: 12411278.4 i/s - 1.36x  (± 0.00) slower

$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   507.960k i/100ms
     each_with_index   969.962k i/100ms
Calculating -------------------------------------
          While Loop      5.067M (± 2.2%) i/s -     25.398M in   5.015219s
     each_with_index      9.472M (± 4.6%) i/s -     47.528M in   5.029275s

Comparison:
     each_with_index:  9472087.5 i/s
          While Loop:  5066640.8 i/s - 1.87x  (± 0.00) slower

$ ruby -v code/enumerable/inject-symbol-vs-block.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   141.059k i/100ms
      inject to_proc   138.456k i/100ms
        inject block   141.430k i/100ms
Calculating -------------------------------------
       inject symbol      1.400M (± 2.9%) i/s -      7.053M in   5.043498s
      inject to_proc      1.423M (± 2.0%) i/s -      7.200M in   5.062744s
        inject block      1.418M (± 2.0%) i/s -      7.213M in   5.087024s

Comparison:
      inject to_proc:  1422695.7 i/s
        inject block:  1418493.7 i/s - same-ish: difference falls within error
       inject symbol:  1399630.1 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    22.159k i/100ms
   Array#map.flatten    25.092k i/100ms
      Array#flat_map    58.620k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    221.647k (± 2.1%) i/s -      1.108M in   5.001007s
   Array#map.flatten    248.176k (± 2.3%) i/s -      1.255M in   5.057946s
      Array#flat_map    586.038k (± 3.2%) i/s -      2.931M in   5.006904s

Comparison:
      Array#flat_map:   586038.0 i/s
   Array#map.flatten:   248175.8 i/s - 2.36x  (± 0.00) slower
Array#map.flatten(1):   221647.0 i/s - 2.64x  (± 0.00) slower

$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   171.639k i/100ms
  Array#reverse_each   507.913k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.260M (± 2.2%) i/s -     11.328M in   5.015668s
  Array#reverse_each      4.997M (± 4.4%) i/s -     25.396M in   5.092924s

Comparison:
  Array#reverse_each:  4997281.6 i/s
  Array#reverse.each:  2259647.9 i/s - 2.21x  (± 0.00) slower

$ ruby -v code/enumerable/select-first-vs-detect.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       720.598k i/100ms
   Enumerable#detect     4.881M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          6.992M (± 5.7%) i/s -    139.796M in  20.086584s
   Enumerable#detect     49.400M (± 3.6%) i/s -    990.932M in  20.087377s

Comparison:
   Enumerable#detect: 49399722.8 i/s
Enumerable#select.first:  6992392.4 i/s - 7.06x  (± 0.00) slower

$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       160.598k i/100ms
Enumerable#select.last
                       397.173k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.419M (± 5.2%) i/s -     12.205M in   5.061258s
Enumerable#select.last
                          4.019M (± 3.2%) i/s -     20.256M in   5.044949s

Comparison:
Enumerable#select.last:  4019341.5 i/s
Enumerable#reverse.detect:  2418682.2 i/s - 1.66x  (± 0.00) slower

$ ruby -v code/enumerable/sort-vs-sort_by.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         1.961k i/100ms
  Enumerable#sort_by     4.231k i/100ms
     Enumerable#sort     1.739k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         52.314k (±18.0%) i/s -    225.515k in   5.006335s
  Enumerable#sort_by     52.718k (±18.4%) i/s -    241.167k in   5.059102s
     Enumerable#sort     67.994k (± 4.9%) i/s -    339.105k in   4.999748s

Comparison:
     Enumerable#sort:    67994.0 i/s
  Enumerable#sort_by:    52718.0 i/s - 1.29x  (± 0.00) slower
Enumerable#sort_by (Symbol#to_proc):    52314.3 i/s - 1.30x  (± 0.00) slower

$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   305.517k i/100ms
Enumerable#sort_by...first
                         7.875k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      3.359M (± 4.2%) i/s -     16.803M in   5.011589s
Enumerable#sort_by...first
                        102.291k (± 4.0%) i/s -    511.875k in   5.012522s

Comparison:
   Enumerable#min_by:  3359022.4 i/s
Enumerable#sort_by...first:   102290.5 i/s - 32.84x  (± 0.00) slower

$ ruby -v code/hash/bracket-vs-dup.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   596.240k i/100ms
            Hash#dup   602.879k i/100ms
Calculating -------------------------------------
              Hash[]      5.862M (± 7.2%) i/s -     29.216M in   5.023808s
            Hash#dup      5.816M (± 9.2%) i/s -     28.938M in   5.043441s

Comparison:
              Hash[]:  5862309.7 i/s
            Hash#dup:  5816331.6 i/s - same-ish: difference falls within error

$ ruby -v code/hash/bracket-vs-fetch.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   295.932M i/100ms
  Hash#fetch, symbol   216.387M i/100ms
     Hash#[], string     8.385M i/100ms
  Hash#fetch, string     7.605M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      3.415B (± 3.1%) i/s -     17.164B in   5.030850s
  Hash#fetch, symbol      2.162B (± 1.8%) i/s -     10.819B in   5.005417s
     Hash#[], string     82.566M (± 2.5%) i/s -    419.263M in   5.081108s
  Hash#fetch, string     75.751M (± 2.1%) i/s -    380.227M in   5.021742s

Comparison:
     Hash#[], symbol: 3415236651.2 i/s
  Hash#fetch, symbol: 2162234471.0 i/s - 1.58x  (± 0.00) slower
     Hash#[], string: 82566351.5 i/s - 41.36x  (± 0.00) slower
  Hash#fetch, string: 75750649.9 i/s - 45.09x  (± 0.00) slower

$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig   995.601k i/100ms
             Hash#[]     5.321M i/100ms
          Hash#[] ||     5.271M i/100ms
          Hash#[] &&     5.182M i/100ms
          Hash#fetch     4.981M i/100ms
 Hash#fetch fallback     4.820M i/100ms
Calculating -------------------------------------
            Hash#dig      9.818M (± 3.0%) i/s -     49.780M in   5.074901s
             Hash#[]     52.207M (± 3.1%) i/s -    260.752M in   4.999690s
          Hash#[] ||     52.145M (± 2.8%) i/s -    263.530M in   5.058113s
          Hash#[] &&     51.665M (± 4.2%) i/s -    259.082M in   5.024551s
          Hash#fetch     49.440M (± 1.9%) i/s -    249.039M in   5.039110s
 Hash#fetch fallback     49.268M (± 3.0%) i/s -    250.634M in   5.091912s

Comparison:
             Hash#[]: 52207043.3 i/s
          Hash#[] ||: 52144617.3 i/s - same-ish: difference falls within error
          Hash#[] &&: 51665188.9 i/s - same-ish: difference falls within error
          Hash#fetch: 49439962.3 i/s - 1.06x  (± 0.00) slower
 Hash#fetch fallback: 49268366.7 i/s - same-ish: difference falls within error
            Hash#dig:  9818362.4 i/s - 5.32x  (± 0.00) slower

$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   344.172M i/100ms
  Hash#fetch + block   214.837M i/100ms
    Hash#fetch + arg   346.751M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      3.400B (± 2.5%) i/s -     17.209B in   5.065347s
  Hash#fetch + block      2.138B (± 2.7%) i/s -     10.742B in   5.027257s
    Hash#fetch + arg      3.436B (± 2.4%) i/s -     17.338B in   5.048679s

Comparison:
    Hash#fetch + arg: 3436140538.5 i/s
  Hash#fetch + const: 3399534077.8 i/s - same-ish: difference falls within error
  Hash#fetch + block: 2138319941.2 i/s - 1.61x  (± 0.00) slower

$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h     8.224k i/100ms
         sort + to_h     3.622k i/100ms
Calculating -------------------------------------
      sort_by + to_h    302.792k (±48.0%) i/s -      1.044M in   5.012733s
         sort + to_h     84.405k (± 3.4%) i/s -    423.774k in   5.026616s

Comparison:
      sort_by + to_h:   302792.2 i/s
         sort + to_h:    84404.9 i/s - 3.59x  (± 0.00) slower

$ ruby -v code/hash/keys-each-vs-each_key.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each   238.225k i/100ms
       Hash#each_key   269.507k i/100ms
Calculating -------------------------------------
      Hash#keys.each      2.394M (± 4.4%) i/s -     12.149M in   5.085179s
       Hash#each_key      2.673M (± 5.4%) i/s -     13.475M in   5.056527s

Comparison:
       Hash#each_key:  2673192.7 i/s
      Hash#keys.each:  2394227.7 i/s - 1.12x  (± 0.00) slower

$ ruby -v code/hash/keys-include-vs-key.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?   102.000  i/100ms
           Hash#key?     4.466M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      4.650k (±11.1%) i/s -     22.950k in   5.017286s
           Hash#key?     44.604M (± 2.9%) i/s -    223.290M in   5.010381s

Comparison:
           Hash#key?: 44603775.8 i/s
  Hash#keys.include?:     4649.8 i/s - 9592.68x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-[]=.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    11.564k i/100ms
            Hash#[]=    53.451k i/100ms
Calculating -------------------------------------
         Hash#merge!    534.017k (± 4.7%) i/s -      2.671M in   5.013936s
            Hash#[]=    537.265k (± 3.8%) i/s -      2.726M in   5.081709s

Comparison:
            Hash#[]=:   537264.9 i/s
         Hash#merge!:   534016.6 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                        10.363k i/100ms
      Hash#merge({})    15.602k i/100ms
 Hash#dup#merge!({})    16.941k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        267.855k (± 7.3%) i/s -      1.347M in   5.090404s
      Hash#merge({})    163.396k (± 6.8%) i/s -    811.304k in   5.003302s
 Hash#dup#merge!({})    265.300k (± 3.6%) i/s -      1.338M in   5.051586s

Comparison:
{}#merge!(Hash) do end:   267855.2 i/s
 Hash#dup#merge!({}):   265300.3 i/s - same-ish: difference falls within error
      Hash#merge({}):   163395.5 i/s - 1.64x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-double-splat-operator.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   181.754M i/100ms
          Hash#merge   207.965M i/100ms
Calculating -------------------------------------
        Hash#**other      2.145B (± 2.3%) i/s -     10.723B in   5.002425s
          Hash#merge      2.151B (± 2.7%) i/s -     10.814B in   5.032362s

Comparison:
          Hash#merge: 2150603133.1 i/s
        Hash#**other: 2144805318.3 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-vs-merge-bang.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge   673.000  i/100ms
         Hash#merge!    53.841k i/100ms
Calculating -------------------------------------
          Hash#merge      9.167k (± 7.1%) i/s -     45.764k in   5.038606s
         Hash#merge!    520.236k (± 6.4%) i/s -      2.584M in   4.999337s

Comparison:
         Hash#merge!:   520236.4 i/s
          Hash#merge:     9167.1 i/s - 56.75x  (± 0.00) slower

$ ruby -v code/hash/slice-native-vs-before-native.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice        2.001M i/100ms
Array#each               1.575M i/100ms
Array#each_w/_object     1.534M i/100ms
Hash#select-include      2.190M i/100ms
Calculating -------------------------------------
Hash#native-slice        20.000M (± 2.4%) i/s -    100.069M in   5.006455s
Array#each               15.865M (± 2.0%) i/s -     80.332M in   5.065487s
Array#each_w/_object     15.223M (± 4.3%) i/s -     76.724M in   5.049801s
Hash#select-include      22.257M (± 3.8%) i/s -    111.707M in   5.026578s

Comparison:
Hash#select-include : 22257241.4 i/s
Hash#native-slice   : 19999995.6 i/s - 1.11x  (± 0.00) slower
Array#each          : 15865006.0 i/s - 1.40x  (± 0.00) slower
Array#each_w/_object: 15223230.2 i/s - 1.46x  (± 0.00) slower

$ ruby -v code/hash/values-include-vs-value.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?    49.000  i/100ms
         Hash#value?   138.000  i/100ms
Calculating -------------------------------------
Hash#values.include?      3.552k (±11.3%) i/s -     17.395k in   4.994524s
         Hash#value?      8.330k (± 5.4%) i/s -     41.538k in   5.001873s

Comparison:
         Hash#value?:     8330.0 i/s
Hash#values.include?:     3552.1 i/s - 2.35x  (± 0.00) slower

$ ruby -v code/method/call-vs-send-vs-method_missing.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   213.349M i/100ms
                send   213.898M i/100ms
      method_missing   214.695M i/100ms
Calculating -------------------------------------
                call      2.159B (± 2.2%) i/s -     10.881B in   5.042586s
                send      2.149B (± 2.6%) i/s -     10.909B in   5.080931s
      method_missing      2.152B (± 2.2%) i/s -     10.949B in   5.089512s

Comparison:
                call: 2158800820.9 i/s
      method_missing: 2152401160.2 i/s - same-ish: difference falls within error
                send: 2148536429.5 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/block-vs-to_proc.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    62.674k i/100ms
      Symbol#to_proc    64.279k i/100ms
Calculating -------------------------------------
               Block    673.963k (± 9.7%) i/s -      3.322M in   5.004545s
      Symbol#to_proc    673.731k (± 8.9%) i/s -      3.343M in   5.025138s

Comparison:
               Block:   673963.0 i/s
      Symbol#to_proc:   673730.6 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   317.648M i/100ms
       block + yield   349.593M i/100ms
        unused block   351.656M i/100ms
               yield   346.295M i/100ms
Calculating -------------------------------------
          block.call      3.411B (± 3.8%) i/s -     17.153B in   5.037047s
       block + yield      3.450B (± 2.6%) i/s -     17.480B in   5.070772s
        unused block      3.457B (± 1.9%) i/s -     17.583B in   5.088324s
               yield      3.448B (± 1.8%) i/s -     17.315B in   5.023747s

Comparison:
        unused block: 3456806176.9 i/s
       block + yield: 3449668104.3 i/s - same-ish: difference falls within error
               yield: 3447753754.4 i/s - same-ish: difference falls within error
          block.call: 3410697404.9 i/s - same-ish: difference falls within error

$ ruby -v code/range/cover-vs-include.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?     4.909M i/100ms
      range#include?     5.290k i/100ms
       range#member?     5.854k i/100ms
       plain compare     6.881M i/100ms
Calculating -------------------------------------
        range#cover?     47.002M (±11.3%) i/s -    230.740M in   5.036121s
      range#include?     86.186k (± 3.0%) i/s -    433.780k in   5.037711s
       range#member?     86.394k (± 2.6%) i/s -    433.196k in   5.017808s
       plain compare     67.290M (± 2.1%) i/s -    337.167M in   5.012917s

Comparison:
       plain compare: 67289996.5 i/s
        range#cover?: 47001794.2 i/s - 1.43x  (± 0.00) slower
       range#member?:    86393.6 i/s - 778.88x  (± 0.00) slower
      range#include?:    86185.7 i/s - 780.76x  (± 0.00) slower

$ ruby -v code/string/===-vs-=~-vs-match.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     1.495M i/100ms
           String#=~     1.513M i/100ms
          Regexp#===     1.509M i/100ms
        String#match     1.464M i/100ms
Calculating -------------------------------------
       String#match?     14.439M (± 5.9%) i/s -     73.240M in   5.091374s
           String#=~     14.758M (± 4.4%) i/s -     74.122M in   5.032639s
          Regexp#===     14.752M (± 4.2%) i/s -     73.947M in   5.021814s
        String#match     14.340M (± 4.3%) i/s -     71.715M in   5.011199s

Comparison:
           String#=~: 14757667.1 i/s
          Regexp#===: 14752157.6 i/s - same-ish: difference falls within error
       String#match?: 14438961.3 i/s - same-ish: difference falls within error
        String#match: 14339611.3 i/s - same-ish: difference falls within error

$ ruby -v code/string/casecmp-vs-downcase-==.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.417M i/100ms
      String#casecmp     5.270M i/100ms
Calculating -------------------------------------
String#downcase + ==     24.960M (± 4.2%) i/s -    125.667M in   5.044125s
      String#casecmp     51.601M (± 4.0%) i/s -    258.215M in   5.012492s

Comparison:
      String#casecmp: 51601136.3 i/s
String#downcase + ==: 24960225.6 i/s - 2.07x  (± 0.00) slower

$ ruby -v code/string/concatenation.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   192.570M i/100ms
       String#concat   213.081M i/100ms
       String#append   218.551M i/100ms
         "foo" "bar"   217.639M i/100ms
  "#{'foo'}#{'bar'}"   218.967M i/100ms
Calculating -------------------------------------
            String#+      2.147B (± 2.5%) i/s -     10.784B in   5.026922s
       String#concat      2.160B (± 1.9%) i/s -     10.867B in   5.033084s
       String#append      2.111B (± 4.9%) i/s -     10.709B in   5.084967s
         "foo" "bar"      2.150B (± 2.3%) i/s -     10.882B in   5.063929s
  "#{'foo'}#{'bar'}"      2.151B (± 2.5%) i/s -     10.948B in   5.092184s

Comparison:
       String#concat: 2159904680.0 i/s
  "#{'foo'}#{'bar'}": 2151379513.5 i/s - same-ish: difference falls within error
         "foo" "bar": 2150142801.1 i/s - same-ish: difference falls within error
            String#+: 2146588047.3 i/s - same-ish: difference falls within error
       String#append: 2111439732.7 i/s - same-ish: difference falls within error

$ ruby -v code/string/dup-vs-unary-plus.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   343.484M i/100ms
          String#dup   213.147M i/100ms
Calculating -------------------------------------
           String#+@      3.457B (± 2.1%) i/s -     17.518B in   5.069640s
          String#dup      2.139B (± 2.2%) i/s -     10.870B in   5.084001s

Comparison:
           String#+@: 3456964322.8 i/s
          String#dup: 2139193504.4 i/s - 1.62x  (± 0.00) slower

$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   120.380k i/100ms
       String#match?   237.841k i/100ms
    String#end_with?     1.095M i/100ms
Calculating -------------------------------------
           String#=~      2.328M (± 3.1%) i/s -     11.677M in   5.021635s
       String#match?      2.374M (± 2.4%) i/s -     11.892M in   5.013091s
    String#end_with?     10.737M (± 1.9%) i/s -     53.678M in   5.001016s

Comparison:
    String#end_with?: 10737351.4 i/s
       String#match?:  2373661.6 i/s - 4.52x  (± 0.00) slower
           String#=~:  2327753.3 i/s - 4.61x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-sub.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    14.256k i/100ms
          String#sub    88.288k i/100ms
String#dup["string"]=
                         6.973M i/100ms
Calculating -------------------------------------
         String#gsub    939.869k (± 6.4%) i/s -      4.676M in   4.998188s
          String#sub    893.738k (± 2.8%) i/s -      4.503M in   5.042417s
String#dup["string"]=
                         69.323M (± 2.0%) i/s -    348.669M in   5.031652s

Comparison:
String#dup["string"]=: 69323039.4 i/s
         String#gsub:   939868.6 i/s - 73.76x  (± 0.00) slower
          String#sub:   893738.1 i/s - 77.57x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-tr.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub     6.844k i/100ms
           String#tr   302.917k i/100ms
Calculating -------------------------------------
         String#gsub      2.926M (±10.5%) i/s -     14.407M in   4.994888s
           String#tr      2.986M (± 2.4%) i/s -     15.146M in   5.074647s

Comparison:
           String#tr:  2986281.3 i/s
         String#gsub:  2925569.0 i/s - same-ish: difference falls within error

$ ruby -v code/string/mutable_vs_immutable_strings.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze   202.380M i/100ms
         With Freeze   213.658M i/100ms
Calculating -------------------------------------
      Without Freeze      2.137B (± 2.8%) i/s -     10.726B in   5.023979s
         With Freeze      2.156B (± 1.9%) i/s -     10.897B in   5.055589s

Comparison:
         With Freeze: 2156111345.7 i/s
      Without Freeze: 2136683985.7 i/s - same-ish: difference falls within error

$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/     1.830k i/100ms
      String#squeeze    67.523k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     55.567k (± 3.3%) i/s -    278.160k in   5.011253s
      String#squeeze    664.984k (± 2.4%) i/s -      3.376M in   5.080032s

Comparison:
      String#squeeze:   664984.3 i/s
 String#gsub/regex+/:    55567.1 i/s - 11.97x  (± 0.00) slower

$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   588.678k i/100ms
       String#match?   753.134k i/100ms
  String#start_with?     3.070M i/100ms
Calculating -------------------------------------
           String#=~      7.409M (± 2.5%) i/s -     37.087M in   5.008764s
       String#match?      7.455M (± 3.8%) i/s -     37.657M in   5.058987s
  String#start_with?     30.110M (± 4.3%) i/s -    150.421M in   5.005523s

Comparison:
  String#start_with?: 30110362.7 i/s
       String#match?:  7454831.0 i/s - 4.04x  (± 0.00) slower
           String#=~:  7409220.1 i/s - 4.06x  (± 0.00) slower

$ ruby -v code/string/start_with-vs-substring-==.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?   417.084k i/100ms
    String#[0, n] ==   473.065k i/100ms
   String#[RANGE] ==    19.139k i/100ms
   String#[0...n] ==   352.891k i/100ms
Calculating -------------------------------------
  String#start_with?      5.817M (± 4.2%) i/s -     29.196M in   5.028034s
    String#[0, n] ==      4.799M (± 5.4%) i/s -     24.126M in   5.048933s
   String#[RANGE] ==      4.747M (± 9.0%) i/s -     23.503M in   4.998041s
   String#[0...n] ==      3.479M (± 4.5%) i/s -     17.645M in   5.082459s

Comparison:
  String#start_with?:  5817325.5 i/s
    String#[0, n] ==:  4798530.0 i/s - 1.21x  (± 0.00) slower
   String#[RANGE] ==:  4746810.8 i/s - 1.23x  (± 0.00) slower
   String#[0...n] ==:  3478809.5 i/s - 1.67x  (± 0.00) slower

$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=     6.532M i/100ms
 String#sub!'string'    90.248k i/100ms
String#gsub!'string'    88.130k i/100ms
  String#[/regexp/]=   461.309k i/100ms
 String#sub!/regexp/   666.603k i/100ms
String#gsub!/regexp/     6.208k i/100ms
Calculating -------------------------------------
  String#['string']=     66.475M (± 2.2%) i/s -    333.144M in   5.013944s
 String#sub!'string'    918.005k (± 2.3%) i/s -      4.603M in   5.016545s
String#gsub!'string'    977.549k (± 2.4%) i/s -      4.935M in   5.051555s
  String#[/regexp/]=      4.581M (± 2.2%) i/s -     23.065M in   5.037909s
 String#sub!/regexp/      6.625M (± 3.7%) i/s -     33.330M in   5.038226s
String#gsub!/regexp/      2.631M (±10.9%) i/s -     12.937M in   4.996638s

Comparison:
  String#['string']=: 66475195.8 i/s
 String#sub!/regexp/:  6625105.2 i/s - 10.03x  (± 0.00) slower
  String#[/regexp/]=:  4580662.6 i/s - 14.51x  (± 0.00) slower
String#gsub!/regexp/:  2631346.6 i/s - 25.26x  (± 0.00) slower
String#gsub!'string':   977548.7 i/s - 68.00x  (± 0.00) slower
 String#sub!'string':   918005.4 i/s - 72.41x  (± 0.00) slower

$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub   561.829k i/100ms
        String#chomp     2.320M i/100ms
String#delete_suffix     2.350M i/100ms
Calculating -------------------------------------
          String#sub      5.582M (± 2.4%) i/s -     28.091M in   5.035987s
        String#chomp     22.747M (± 3.8%) i/s -    113.677M in   5.005152s
String#delete_suffix     24.588M (± 4.9%) i/s -    124.545M in   5.078359s

Comparison:
String#delete_suffix: 24588148.4 i/s
        String#chomp: 22746707.3 i/s - same-ish: difference falls within error
          String#sub:  5581550.5 i/s - 4.41x  (± 0.00) slower

$ ruby -v code/string/sub-vs-delete_prefix.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     2.499M i/100ms
          String#sub   623.319k i/100ms
Calculating -------------------------------------
String#delete_prefix     26.116M (± 5.1%) i/s -    132.439M in   5.085523s
          String#sub      6.078M (± 4.3%) i/s -     30.543M in   5.035284s

Comparison:
String#delete_prefix: 26116194.7 i/s
          String#sub:  6077668.0 i/s - 4.30x  (± 0.00) slower

$ ruby -v code/string/unpack1-vs-unpack[0].rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     1.283M i/100ms
    String#unpack[0]     2.012M i/100ms
Calculating -------------------------------------
      String#unpack1     20.057M (± 4.8%) i/s -    100.111M in   5.003760s
    String#unpack[0]     20.360M (± 1.8%) i/s -    102.592M in   5.040571s

Comparison:
    String#unpack[0]: 20359884.6 i/s
      String#unpack1: 20057237.2 i/s - same-ish: difference falls within error

$ ruby -v code/time/iso8601-vs-parse.rb
truffleruby 20.3.0-dev-1fb68a0e, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601     3.089k i/100ms
          Time.parse   720.000  i/100ms
Calculating -------------------------------------
        Time.iso8601    325.751k (± 8.0%) i/s -      1.616M in   4.996070s
          Time.parse     42.032k (± 7.1%) i/s -    209.520k in   5.011409s

Comparison:
        Time.iso8601:   325751.0 i/s
          Time.parse:    42032.0 i/s - 7.75x  (± 0.00) slower
```



## License

![CC-BY-SA](CC-BY-SA.png)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Code License

### CC0 1.0 Universal

To the extent possible under law, @JuanitoFatas has waived all copyright and related or neighboring rights to "fast-ruby".

This work belongs to the community.
