## Fast TruffleRuby 


The idea of this project is to run all collected examples from [Fast Ruby](https://github.com/JuanitoFatas/fast-ruby) and run it against the latest TruffleRuby version to see if the same results hold for TruffleRuby.

As you will see in the results below, some results a quite different

## Results
```
$ ruby -v code/general/array-argument-vs-splat-arguments.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       224.555M i/100ms
Function with splat arguments
                         1.463k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          2.042B (± 5.0%) i/s -     10.330B in   5.072328s
Function with splat arguments
                         14.182k (± 5.4%) i/s -     71.687k in   5.069660s

Comparison:
Function with single Array argument: 2041937225.9 i/s
Function with splat arguments:    14182.0 i/s - 143980.78x  (± 0.00) slower

$ ruby -v code/general/assignment.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   163.515M i/100ms
Sequential Assignment
                       207.387M i/100ms
Calculating -------------------------------------
 Parallel Assignment      2.069B (± 5.5%) i/s -     10.465B in   5.073695s
Sequential Assignment
                          2.066B (± 6.8%) i/s -     10.369B in   5.042675s

Comparison:
 Parallel Assignment: 2068947002.4 i/s
Sequential Assignment: 2066419921.9 i/s - same-ish: difference falls within error

$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   215.180M i/100ms
       attr_accessor   209.098M i/100ms
Calculating -------------------------------------
   getter_and_setter      2.160B (± 1.5%) i/s -     10.974B in   5.082216s
       attr_accessor      2.155B (± 2.6%) i/s -     10.873B in   5.048249s

Comparison:
   getter_and_setter: 2159832850.3 i/s
       attr_accessor: 2155448421.4 i/s - same-ish: difference falls within error

$ ruby -v code/general/begin-rescue-vs-respond-to.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     9.433k i/100ms
         respond_to?   214.427M i/100ms
Calculating -------------------------------------
      begin...rescue     95.662k (± 2.9%) i/s -    481.083k in   5.033525s
         respond_to?      2.090B (± 4.3%) i/s -     10.507B in   5.037574s

Comparison:
         respond_to?: 2089686522.1 i/s
      begin...rescue:    95662.0 i/s - 21844.48x  (± 0.00) slower

$ ruby -v code/general/block-apply-method.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   181.964M i/100ms
             &method   218.900M i/100ms
Calculating -------------------------------------
              normal      2.137B (± 3.1%) i/s -     10.736B in   5.028390s
             &method      2.156B (± 3.2%) i/s -     10.945B in   5.080819s

Comparison:
             &method: 2156472193.6 i/s
              normal: 2137128180.7 i/s - same-ish: difference falls within error

$ ruby -v code/general/define_method-vs-module-eval.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                       205.000  i/100ms
       define_method   146.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.398k (±36.1%) i/s -      6.560k in   6.406079s
       define_method      4.021k (±34.6%) i/s -     14.454k in   5.026826s

Comparison:
       define_method:     4021.2 i/s
module_eval with string:     1398.4 i/s - 2.88x  (± 0.00) slower

$ ruby -v code/general/format-vs-round-and-to-s.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    57.653k i/100ms
       Kernel#format    76.190k i/100ms
            String#%    74.240k i/100ms
Calculating -------------------------------------
         Float#round    566.975k (± 4.1%) i/s -      2.883M in   5.093530s
       Kernel#format    758.430k (± 2.6%) i/s -      3.810M in   5.026262s
            String#%    764.477k (± 1.6%) i/s -      3.860M in   5.051134s

Comparison:
            String#%:   764477.0 i/s
       Kernel#format:   758429.8 i/s - same-ish: difference falls within error
         Float#round:   566974.6 i/s - 1.35x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct-on-access.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   344.942M i/100ms
          OpenStruct    71.919M i/100ms
Calculating -------------------------------------
                Hash      3.545B (± 1.6%) i/s -     17.937B in   5.060674s
          OpenStruct    721.011M (± 3.2%) i/s -      3.668B in   5.092564s

Comparison:
                Hash: 3545354858.7 i/s
          OpenStruct: 721010864.4 i/s - 4.92x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   211.541M i/100ms
          OpenStruct   212.061M i/100ms
Calculating -------------------------------------
                Hash      2.213B (± 2.2%) i/s -     11.212B in   5.068140s
          OpenStruct      2.191B (± 3.2%) i/s -     11.027B in   5.039096s

Comparison:
                Hash: 2213379284.6 i/s
          OpenStruct: 2190764069.3 i/s - same-ish: difference falls within error

$ ruby -v code/general/inheritance-check.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal     1.353M i/100ms
  ancestors.include?   201.207k i/100ms
Calculating -------------------------------------
  less than or equal     13.503M (± 1.7%) i/s -     67.664M in   5.012561s
  ancestors.include?      1.995M (± 2.2%) i/s -     10.060M in   5.045488s

Comparison:
  less than or equal: 13502696.8 i/s
  ancestors.include?:  1994941.7 i/s - 6.77x  (± 0.00) slower

$ ruby -v code/general/loop-vs-while-true.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     3.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     35.522  (± 2.8%) i/s -    180.000  in   5.070508s
         Kernel loop      8.164  (± 0.0%) i/s -     41.000  in   5.024215s

Comparison:
          While Loop:       35.5 i/s
         Kernel loop:        8.2 i/s - 4.35x  (± 0.00) slower

$ ruby -v code/general/raise-vs-e2mmap.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
<internal:core> core/kernel.rb:236:in `gem_original_require': cannot load such file -- e2mmap (LoadError)
	from code/general/raise-vs-e2mmap.rb:2:in `<main>'
$ ruby -v code/array/array-first-vs-index.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   223.221M i/100ms
         Array#first   224.313M i/100ms
Calculating -------------------------------------
           Array#[0]      2.229B (± 0.8%) i/s -     11.161B in   5.006379s
         Array#first      2.214B (± 2.1%) i/s -     11.216B in   5.069270s

Comparison:
           Array#[0]: 2229495280.0 i/s
         Array#first: 2213545328.6 i/s - same-ish: difference falls within error

$ ruby -v code/array/array-last-vs-index.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   354.900M i/100ms
          Array#last   355.194M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.538B (± 2.5%) i/s -     17.745B in   5.018631s
          Array#last      3.542B (± 2.5%) i/s -     17.760B in   5.018207s

Comparison:
          Array#last: 3541564486.0 i/s
          Array#[-1]: 3538309290.5 i/s - same-ish: difference falls within error

$ ruby -v code/array/bsearch-vs-find.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   403.207k i/100ms
Calculating -------------------------------------
                find      0.111  (± 0.0%) i/s -      1.000  in   9.011486s
             bsearch      4.034M (±10.0%) i/s -     20.160M in   5.076342s

Comparison:
             bsearch:  4034408.6 i/s
                find:        0.1 i/s - 36356015.34x  (± 0.00) slower

$ ruby -v code/array/insert-vs-unshift.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.168  (± 0.0%) i/s -      1.000  in   5.937230s
        Array#insert      0.318  (± 0.0%) i/s -      2.000  in   6.286884s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.89x  (± 0.00) slower

$ ruby -v code/array/length-vs-size-vs-count.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   353.927M i/100ms
          Array#size   355.837M i/100ms
         Array#count   357.212M i/100ms
Calculating -------------------------------------
        Array#length      3.354B (± 2.5%) i/s -     16.988B in   5.068600s
          Array#size      3.523B (± 3.0%) i/s -     17.792B in   5.054850s
         Array#count      3.463B (± 4.8%) i/s -     17.503B in   5.066427s

Comparison:
          Array#size: 3523061159.5 i/s
         Array#count: 3463141613.1 i/s - same-ish: difference falls within error
        Array#length: 3353781303.8 i/s - same-ish: difference falls within error

$ ruby -v code/array/shuffle-first-vs-sample.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    35.890k i/100ms
        Array#sample     3.591M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    344.552k (± 2.6%) i/s -      1.723M in   5.003197s
        Array#sample     33.486M (± 5.1%) i/s -    168.756M in   5.053370s

Comparison:
        Array#sample: 33485538.6 i/s
 Array#shuffle.first:   344552.1 i/s - 97.19x  (± 0.00) slower

$ ruby -v code/date/iso8601-vs-parse.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601     2.048k i/100ms
          Date.parse     2.415k i/100ms
Calculating -------------------------------------
        Date.iso8601     31.671k (± 6.8%) i/s -    157.696k in   5.001313s
          Date.parse     32.789k (± 6.6%) i/s -    164.220k in   5.029240s

Comparison:
          Date.parse:    32788.5 i/s
        Date.iso8601:    31671.1 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/each-push-vs-map.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   284.642k i/100ms
           Array#map   668.618k i/100ms
Calculating -------------------------------------
   Array#each + push      2.885M (± 2.5%) i/s -     14.517M in   5.035248s
           Array#map      6.642M (± 2.7%) i/s -     33.431M in   5.037112s

Comparison:
           Array#map:  6641812.8 i/s
   Array#each + push:  2884795.7 i/s - 2.30x  (± 0.00) slower

$ ruby -v code/enumerable/each-vs-for-loop.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop     1.117M i/100ms
               #each     1.559M i/100ms
Calculating -------------------------------------
            For loop     11.084M (± 2.1%) i/s -     55.848M in   5.040973s
               #each     16.050M (± 1.5%) i/s -     81.049M in   5.051148s

Comparison:
               #each: 16049556.4 i/s
            For loop: 11083974.1 i/s - 1.45x  (± 0.00) slower

$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   460.569k i/100ms
     each_with_index     1.112M i/100ms
Calculating -------------------------------------
          While Loop      4.494M (± 2.6%) i/s -     22.568M in   5.025006s
     each_with_index     10.861M (± 2.6%) i/s -     54.500M in   5.021375s

Comparison:
     each_with_index: 10861226.3 i/s
          While Loop:  4494268.6 i/s - 2.42x  (± 0.00) slower

$ ruby -v code/enumerable/inject-symbol-vs-block.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   188.474k i/100ms
      inject to_proc   188.615k i/100ms
        inject block   191.134k i/100ms
Calculating -------------------------------------
       inject symbol      1.904M (± 2.0%) i/s -      9.612M in   5.050987s
      inject to_proc      1.908M (± 1.4%) i/s -      9.619M in   5.041669s
        inject block      1.911M (± 1.1%) i/s -      9.557M in   5.000440s

Comparison:
        inject block:  1911405.2 i/s
      inject to_proc:  1908363.7 i/s - same-ish: difference falls within error
       inject symbol:  1903847.5 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    20.207k i/100ms
   Array#map.flatten    19.960k i/100ms
      Array#flat_map    52.997k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    223.596k (± 7.9%) i/s -      1.111M in   5.002371s
   Array#map.flatten    229.287k (± 5.3%) i/s -      1.158M in   5.064376s
      Array#flat_map    582.155k (± 3.6%) i/s -      2.915M in   5.013711s

Comparison:
      Array#flat_map:   582155.2 i/s
   Array#map.flatten:   229286.7 i/s - 2.54x  (± 0.00) slower
Array#map.flatten(1):   223595.9 i/s - 2.60x  (± 0.00) slower

$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   192.546k i/100ms
  Array#reverse_each   568.578k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.098M (± 8.3%) i/s -     10.590M in   5.087162s
  Array#reverse_each      5.283M (± 8.2%) i/s -     26.723M in   5.095836s

Comparison:
  Array#reverse_each:  5282865.2 i/s
  Array#reverse.each:  2097548.3 i/s - 2.52x  (± 0.00) slower

$ ruby -v code/enumerable/select-first-vs-detect.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       651.855k i/100ms
   Enumerable#detect     4.045M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          6.409M (± 4.5%) i/s -    128.415M in  20.079772s
   Enumerable#detect     38.724M (± 2.4%) i/s -    776.727M in  20.069992s

Comparison:
   Enumerable#detect: 38723545.3 i/s
Enumerable#select.first:  6408918.2 i/s - 6.04x  (± 0.00) slower

$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       209.893k i/100ms
Enumerable#select.last
                       353.116k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.051M (± 3.1%) i/s -     10.285M in   5.019298s
Enumerable#select.last
                          3.678M (± 2.4%) i/s -     18.715M in   5.091858s

Comparison:
Enumerable#select.last:  3677727.4 i/s
Enumerable#reverse.detect:  2051099.3 i/s - 1.79x  (± 0.00) slower

$ ruby -v code/enumerable/sort-vs-sort_by.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         3.849k i/100ms
  Enumerable#sort_by     3.865k i/100ms
     Enumerable#sort     4.887k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         46.353k (± 7.7%) i/s -    230.940k in   5.017649s
  Enumerable#sort_by     47.419k (± 9.3%) i/s -    235.765k in   5.024182s
     Enumerable#sort     66.978k (± 2.4%) i/s -    337.203k in   5.037608s

Comparison:
     Enumerable#sort:    66977.9 i/s
  Enumerable#sort_by:    47418.7 i/s - 1.41x  (± 0.00) slower
Enumerable#sort_by (Symbol#to_proc):    46353.1 i/s - 1.44x  (± 0.00) slower

$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   315.960k i/100ms
Enumerable#sort_by...first
                         9.457k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      3.324M (± 1.5%) i/s -     16.746M in   5.038765s
Enumerable#sort_by...first
                        104.645k (± 3.9%) i/s -    529.592k in   5.068955s

Comparison:
   Enumerable#min_by:  3324232.5 i/s
Enumerable#sort_by...first:   104644.6 i/s - 31.77x  (± 0.00) slower

$ ruby -v code/hash/bracket-vs-dup.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   619.809k i/100ms
            Hash#dup   609.632k i/100ms
Calculating -------------------------------------
              Hash[]      6.095M (± 2.3%) i/s -     30.990M in   5.087277s
            Hash#dup      6.023M (± 3.6%) i/s -     30.482M in   5.067218s

Comparison:
              Hash[]:  6095003.8 i/s
            Hash#dup:  6023066.2 i/s - same-ish: difference falls within error

$ ruby -v code/hash/bracket-vs-fetch.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   209.122M i/100ms
  Hash#fetch, symbol   334.268M i/100ms
     Hash#[], string     9.084M i/100ms
  Hash#fetch, string     7.475M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      2.073B (± 2.6%) i/s -     10.456B in   5.046595s
  Hash#fetch, symbol      3.341B (± 1.5%) i/s -     16.713B in   5.003061s
     Hash#[], string     90.862M (± 1.2%) i/s -    463.295M in   5.099686s
  Hash#fetch, string     74.200M (± 3.0%) i/s -    373.735M in   5.041790s

Comparison:
  Hash#fetch, symbol: 3341461782.0 i/s
     Hash#[], symbol: 2073401978.6 i/s - 1.61x  (± 0.00) slower
     Hash#[], string: 90862110.5 i/s - 36.78x  (± 0.00) slower
  Hash#fetch, string: 74200290.7 i/s - 45.03x  (± 0.00) slower

$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig     4.731M i/100ms
             Hash#[]     5.577M i/100ms
          Hash#[] ||     5.612M i/100ms
          Hash#[] &&     5.566M i/100ms
          Hash#fetch     5.264M i/100ms
 Hash#fetch fallback     5.324M i/100ms
Calculating -------------------------------------
            Hash#dig     48.607M (± 1.4%) i/s -    246.037M in   5.062711s
             Hash#[]     55.818M (± 0.8%) i/s -    284.430M in   5.095954s
          Hash#[] ||     55.272M (± 1.5%) i/s -    280.577M in   5.077362s
          Hash#[] &&     55.119M (± 2.8%) i/s -    278.321M in   5.053804s
          Hash#fetch     51.981M (± 3.0%) i/s -    263.188M in   5.068024s
 Hash#fetch fallback     52.924M (± 2.1%) i/s -    266.214M in   5.032596s

Comparison:
             Hash#[]: 55818028.4 i/s
          Hash#[] ||: 55272412.7 i/s - same-ish: difference falls within error
          Hash#[] &&: 55118670.5 i/s - same-ish: difference falls within error
 Hash#fetch fallback: 52923801.5 i/s - 1.05x  (± 0.00) slower
          Hash#fetch: 51981067.0 i/s - 1.07x  (± 0.00) slower
            Hash#dig: 48607407.2 i/s - 1.15x  (± 0.00) slower

$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   207.422M i/100ms
  Hash#fetch + block   198.744M i/100ms
    Hash#fetch + arg   209.861M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      2.079B (± 2.1%) i/s -     10.579B in   5.090359s
  Hash#fetch + block      2.098B (± 0.9%) i/s -     10.533B in   5.022102s
    Hash#fetch + arg      2.090B (± 2.1%) i/s -     10.493B in   5.022688s

Comparison:
  Hash#fetch + block: 2097589251.1 i/s
    Hash#fetch + arg: 2090097726.2 i/s - same-ish: difference falls within error
  Hash#fetch + const: 2079129727.7 i/s - same-ish: difference falls within error

$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h    28.644k i/100ms
         sort + to_h     7.363k i/100ms
Calculating -------------------------------------
      sort_by + to_h    322.623k (± 9.4%) i/s -      1.604M in   5.035329s
         sort + to_h     71.299k (± 5.1%) i/s -    360.787k in   5.072922s

Comparison:
      sort_by + to_h:   322623.5 i/s
         sort + to_h:    71299.3 i/s - 4.52x  (± 0.00) slower

$ ruby -v code/hash/keys-each-vs-each_key.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each   246.685k i/100ms
       Hash#each_key   281.192k i/100ms
Calculating -------------------------------------
      Hash#keys.each      2.253M (± 3.3%) i/s -     11.348M in   5.040838s
       Hash#each_key      2.789M (± 5.1%) i/s -     14.060M in   5.055188s

Comparison:
       Hash#each_key:  2789175.4 i/s
      Hash#keys.each:  2253485.8 i/s - 1.24x  (± 0.00) slower

$ ruby -v code/hash/keys-include-vs-key.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?    85.000  i/100ms
           Hash#key?    11.539M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      1.848k (±31.2%) i/s -      8.755k in   5.021380s
           Hash#key?    113.263M (± 3.7%) i/s -    576.972M in   5.101506s

Comparison:
           Hash#key?: 113262699.5 i/s
  Hash#keys.include?:     1847.8 i/s - 61295.73x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-[]=.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    52.535k i/100ms
            Hash#[]=    48.842k i/100ms
Calculating -------------------------------------
         Hash#merge!    522.058k (± 0.7%) i/s -      2.627M in   5.031808s
            Hash#[]=    535.936k (± 3.4%) i/s -      2.735M in   5.110197s

Comparison:
            Hash#[]=:   535936.4 i/s
         Hash#merge!:   522058.1 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                        27.195k i/100ms
      Hash#merge({})    15.650k i/100ms
 Hash#dup#merge!({})    23.152k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        283.035k (± 4.1%) i/s -      1.414M in   5.004718s
      Hash#merge({})    166.264k (± 3.1%) i/s -    845.100k in   5.087943s
 Hash#dup#merge!({})    244.886k (± 4.3%) i/s -      1.227M in   5.020051s

Comparison:
{}#merge!(Hash) do end:   283034.7 i/s
 Hash#dup#merge!({}):   244885.6 i/s - 1.16x  (± 0.00) slower
      Hash#merge({}):   166264.0 i/s - 1.70x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-double-splat-operator.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   189.313M i/100ms
          Hash#merge   192.085M i/100ms
Calculating -------------------------------------
        Hash#**other      1.983B (± 4.4%) i/s -     10.034B in   5.068107s
          Hash#merge      2.097B (± 1.1%) i/s -     10.565B in   5.039609s

Comparison:
          Hash#merge: 2096594409.2 i/s
        Hash#**other: 1983475331.9 i/s - 1.06x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-merge-bang.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge   878.000  i/100ms
         Hash#merge!    52.643k i/100ms
Calculating -------------------------------------
          Hash#merge      9.143k (± 1.7%) i/s -     46.534k in   5.090942s
         Hash#merge!    543.222k (± 3.8%) i/s -      2.737M in   5.046665s

Comparison:
         Hash#merge!:   543222.4 i/s
          Hash#merge:     9143.3 i/s - 59.41x  (± 0.00) slower

$ ruby -v code/hash/slice-native-vs-before-native.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice        1.730M i/100ms
Array#each               1.435M i/100ms
Array#each_w/_object     1.481M i/100ms
Hash#select-include      2.126M i/100ms
Calculating -------------------------------------
Hash#native-slice        19.033M (± 4.3%) i/s -     95.135M in   5.008210s
Array#each               15.820M (± 3.0%) i/s -     80.369M in   5.085006s
Array#each_w/_object     15.411M (± 4.8%) i/s -     76.989M in   5.007289s
Hash#select-include      21.913M (± 4.5%) i/s -    110.571M in   5.055909s

Comparison:
Hash#select-include : 21913026.0 i/s
Hash#native-slice   : 19033236.7 i/s - 1.15x  (± 0.00) slower
Array#each          : 15819635.4 i/s - 1.39x  (± 0.00) slower
Array#each_w/_object: 15410535.8 i/s - 1.42x  (± 0.00) slower

$ ruby -v code/hash/values-include-vs-value.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?    80.000  i/100ms
         Hash#value?   311.000  i/100ms
Calculating -------------------------------------
Hash#values.include?      1.654k (±16.7%) i/s -      8.160k in   5.024569s
         Hash#value?      7.268k (±22.5%) i/s -     32.966k in   5.007169s

Comparison:
         Hash#value?:     7268.0 i/s
Hash#values.include?:     1653.9 i/s - 4.39x  (± 0.00) slower

$ ruby -v code/method/call-vs-send-vs-method_missing.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   186.811M i/100ms
                send   192.988M i/100ms
      method_missing   192.731M i/100ms
Calculating -------------------------------------
                call      2.063B (± 3.3%) i/s -     10.461B in   5.075686s
                send      2.087B (± 2.1%) i/s -     10.614B in   5.087535s
      method_missing      2.033B (± 3.1%) i/s -     10.215B in   5.029981s

Comparison:
                send: 2087293362.9 i/s
                call: 2063433254.3 i/s - same-ish: difference falls within error
      method_missing: 2032824284.6 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/block-vs-to_proc.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    61.754k i/100ms
      Symbol#to_proc    60.714k i/100ms
Calculating -------------------------------------
               Block    616.693k (± 2.7%) i/s -      3.088M in   5.010717s
      Symbol#to_proc    609.791k (± 2.3%) i/s -      3.096M in   5.080550s

Comparison:
               Block:   616692.5 i/s
      Symbol#to_proc:   609790.6 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   210.635M i/100ms
       block + yield   210.190M i/100ms
        unused block   211.752M i/100ms
               yield   210.068M i/100ms
Calculating -------------------------------------
          block.call      2.068B (± 2.3%) i/s -     10.532B in   5.094452s
       block + yield      2.021B (± 2.9%) i/s -     10.299B in   5.101833s
        unused block      2.068B (± 1.7%) i/s -     10.376B in   5.019743s
               yield      2.075B (± 3.3%) i/s -     10.503B in   5.067071s

Comparison:
               yield: 2075307019.1 i/s
          block.call: 2068463153.8 i/s - same-ish: difference falls within error
        unused block: 2067599039.3 i/s - same-ish: difference falls within error
       block + yield: 2020502575.6 i/s - same-ish: difference falls within error

$ ruby -v code/range/cover-vs-include.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?   306.254M i/100ms
      range#include?    15.032k i/100ms
       range#member?    17.259k i/100ms
       plain compare    34.412M i/100ms
Calculating -------------------------------------
        range#cover?    137.221M (±51.3%) i/s -    918.762M in  11.370618s
      range#include?    189.814k (± 5.5%) i/s -    947.016k in   5.004546s
       range#member?    176.760k (± 3.7%) i/s -    897.468k in   5.083824s
       plain compare    377.429M (± 1.3%) i/s -      1.893B in   5.015416s

Comparison:
       plain compare: 377428913.0 i/s
        range#cover?: 137220606.6 i/s - 2.75x  (± 0.00) slower
      range#include?:   189814.1 i/s - 1988.41x  (± 0.00) slower
       range#member?:   176759.8 i/s - 2135.26x  (± 0.00) slower

$ ruby -v code/string/===-vs-=~-vs-match.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     1.563M i/100ms
           String#=~     1.482M i/100ms
          Regexp#===     1.401M i/100ms
        String#match     1.374M i/100ms
Calculating -------------------------------------
       String#match?     15.185M (± 5.2%) i/s -     76.574M in   5.056433s
           String#=~     15.686M (± 2.5%) i/s -     78.521M in   5.009326s
          Regexp#===     14.067M (± 1.2%) i/s -     71.433M in   5.078801s
        String#match     14.988M (± 4.6%) i/s -     75.565M in   5.052946s

Comparison:
           String#=~: 15685793.8 i/s
       String#match?: 15185235.0 i/s - same-ish: difference falls within error
        String#match: 14988497.4 i/s - same-ish: difference falls within error
          Regexp#===: 14066823.4 i/s - 1.12x  (± 0.00) slower

$ ruby -v code/string/casecmp-vs-downcase-==.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.240M i/100ms
      String#casecmp     4.384M i/100ms
Calculating -------------------------------------
String#downcase + ==     23.414M (± 5.4%) i/s -    118.744M in   5.085777s
      String#casecmp     47.499M (± 1.1%) i/s -    241.114M in   5.076755s

Comparison:
      String#casecmp: 47499275.3 i/s
String#downcase + ==: 23413543.5 i/s - 2.03x  (± 0.00) slower

$ ruby -v code/string/concatenation.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   190.953M i/100ms
       String#concat   195.185M i/100ms
       String#append   192.043M i/100ms
         "foo" "bar"   191.889M i/100ms
  "#{'foo'}#{'bar'}"   210.670M i/100ms
Calculating -------------------------------------
            String#+      2.099B (± 1.4%) i/s -     10.502B in   5.003724s
       String#concat      2.056B (± 3.4%) i/s -     10.345B in   5.037563s
       String#append      2.057B (± 2.2%) i/s -     10.370B in   5.043190s
         "foo" "bar"      2.059B (± 2.6%) i/s -     10.362B in   5.035576s
  "#{'foo'}#{'bar'}"      1.961B (± 5.9%) i/s -      9.902B in   5.066051s

Comparison:
            String#+: 2099312936.6 i/s
         "foo" "bar": 2059230699.0 i/s - same-ish: difference falls within error
       String#append: 2057312925.1 i/s - same-ish: difference falls within error
       String#concat: 2056037084.8 i/s - same-ish: difference falls within error
  "#{'foo'}#{'bar'}": 1961330938.4 i/s - same-ish: difference falls within error

$ ruby -v code/string/dup-vs-unary-plus.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   193.551M i/100ms
          String#dup   192.195M i/100ms
Calculating -------------------------------------
           String#+@      2.017B (± 4.0%) i/s -     10.065B in   4.999178s
          String#dup      2.072B (± 2.7%) i/s -     10.379B in   5.012446s

Comparison:
          String#dup: 2072103037.1 i/s
           String#+@: 2016539049.6 i/s - same-ish: difference falls within error

$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   228.267k i/100ms
       String#match?   206.204k i/100ms
    String#end_with?     6.523M i/100ms
Calculating -------------------------------------
           String#=~      2.141M (± 4.2%) i/s -     10.729M in   5.018993s
       String#match?      2.303M (± 2.0%) i/s -     11.547M in   5.015101s
    String#end_with?     70.276M (± 1.7%) i/s -    352.230M in   5.013578s

Comparison:
    String#end_with?: 70276016.1 i/s
       String#match?:  2303452.2 i/s - 30.51x  (± 0.00) slower
           String#=~:  2141227.4 i/s - 32.82x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-sub.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    80.474k i/100ms
          String#sub    76.306k i/100ms
String#dup["string"]=
                         6.640M i/100ms
Calculating -------------------------------------
         String#gsub    845.940k (± 1.2%) i/s -      4.265M in   5.042561s
          String#sub    777.697k (± 4.0%) i/s -      3.892M in   5.011582s
String#dup["string"]=
                         72.309M (± 1.2%) i/s -    365.222M in   5.051553s

Comparison:
String#dup["string"]=: 72308822.8 i/s
         String#gsub:   845940.5 i/s - 85.48x  (± 0.00) slower
          String#sub:   777696.7 i/s - 92.98x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-tr.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub   150.777k i/100ms
           String#tr   235.770k i/100ms
Calculating -------------------------------------
         String#gsub      2.582M (± 2.6%) i/s -     12.967M in   5.024780s
           String#tr      2.560M (± 2.6%) i/s -     12.967M in   5.068188s

Comparison:
         String#gsub:  2582305.1 i/s
           String#tr:  2560368.6 i/s - same-ish: difference falls within error

$ ruby -v code/string/mutable_vs_immutable_strings.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze   192.825M i/100ms
         With Freeze   193.071M i/100ms
Calculating -------------------------------------
      Without Freeze      1.991B (± 3.8%) i/s -     10.027B in   5.042065s
         With Freeze      2.066B (± 1.8%) i/s -     10.426B in   5.047063s

Comparison:
         With Freeze: 2066392815.5 i/s
      Without Freeze: 1991431768.2 i/s - same-ish: difference falls within error

$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/     4.543k i/100ms
      String#squeeze    53.185k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     54.752k (± 4.2%) i/s -    277.123k in   5.069963s
      String#squeeze    583.718k (± 1.8%) i/s -      2.925M in   5.013027s

Comparison:
      String#squeeze:   583717.6 i/s
 String#gsub/regex+/:    54751.7 i/s - 10.66x  (± 0.00) slower

$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   700.136k i/100ms
       String#match?   694.673k i/100ms
  String#start_with?     2.681M i/100ms
Calculating -------------------------------------
           String#=~      7.037M (± 4.8%) i/s -     35.707M in   5.085540s
       String#match?      7.748M (± 3.6%) i/s -     38.902M in   5.028232s
  String#start_with?     26.779M (± 0.4%) i/s -    134.025M in   5.005005s

Comparison:
  String#start_with?: 26778710.2 i/s
       String#match?:  7747697.7 i/s - 3.46x  (± 0.00) slower
           String#=~:  7037478.3 i/s - 3.81x  (± 0.00) slower

$ ruby -v code/string/start_with-vs-substring-==.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?   480.950k i/100ms
    String#[0, n] ==   154.877k i/100ms
   String#[RANGE] ==   175.106k i/100ms
   String#[0...n] ==   137.034k i/100ms
Calculating -------------------------------------
  String#start_with?      5.266M (± 6.0%) i/s -     26.452M in   5.042739s
    String#[0, n] ==      4.095M (± 8.6%) i/s -     20.444M in   5.028948s
   String#[RANGE] ==      4.022M (± 2.4%) i/s -     20.137M in   5.009300s
   String#[0...n] ==      3.140M (± 2.4%) i/s -     15.759M in   5.020924s

Comparison:
  String#start_with?:  5265605.2 i/s
    String#[0, n] ==:  4095085.8 i/s - 1.29x  (± 0.00) slower
   String#[RANGE] ==:  4022378.4 i/s - 1.31x  (± 0.00) slower
   String#[0...n] ==:  3140390.9 i/s - 1.68x  (± 0.00) slower

$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=     5.956M i/100ms
 String#sub!'string'    77.009k i/100ms
String#gsub!'string'    82.224k i/100ms
  String#[/regexp/]=   534.039k i/100ms
 String#sub!/regexp/   604.583k i/100ms
String#gsub!/regexp/   216.640k i/100ms
Calculating -------------------------------------
  String#['string']=     59.883M (± 3.5%) i/s -    303.765M in   5.078908s
 String#sub!'string'    867.410k (± 6.6%) i/s -      4.390M in   5.083503s
String#gsub!'string'    939.992k (± 4.0%) i/s -      4.769M in   5.081925s
  String#[/regexp/]=      5.517M (± 6.8%) i/s -     27.770M in   5.054712s
 String#sub!/regexp/      6.015M (± 1.1%) i/s -     30.229M in   5.026198s
String#gsub!/regexp/      2.578M (± 2.9%) i/s -     12.998M in   5.046763s

Comparison:
  String#['string']=: 59883364.1 i/s
 String#sub!/regexp/:  6015055.1 i/s - 9.96x  (± 0.00) slower
  String#[/regexp/]=:  5516977.9 i/s - 10.85x  (± 0.00) slower
String#gsub!/regexp/:  2577937.0 i/s - 23.23x  (± 0.00) slower
String#gsub!'string':   939991.9 i/s - 63.71x  (± 0.00) slower
 String#sub!'string':   867410.1 i/s - 69.04x  (± 0.00) slower

$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub   537.141k i/100ms
        String#chomp     4.280M i/100ms
String#delete_suffix     5.643M i/100ms
Calculating -------------------------------------
          String#sub      5.260M (± 1.4%) i/s -     26.320M in   5.005107s
        String#chomp     42.587M (± 1.4%) i/s -    213.990M in   5.025719s
String#delete_suffix     57.517M (± 2.0%) i/s -    287.773M in   5.005357s

Comparison:
String#delete_suffix: 57516867.6 i/s
        String#chomp: 42587413.3 i/s - 1.35x  (± 0.00) slower
          String#sub:  5259633.6 i/s - 10.94x  (± 0.00) slower

$ ruby -v code/string/sub-vs-delete_prefix.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     3.409M i/100ms
          String#sub   634.130k i/100ms
Calculating -------------------------------------
String#delete_prefix     36.217M (± 5.5%) i/s -    180.667M in   5.003679s
          String#sub      6.797M (± 5.2%) i/s -     34.243M in   5.051765s

Comparison:
String#delete_prefix: 36216603.1 i/s
          String#sub:  6797334.2 i/s - 5.33x  (± 0.00) slower

$ ruby -v code/string/unpack1-vs-unpack[0].rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     1.868M i/100ms
    String#unpack[0]     1.853M i/100ms
Calculating -------------------------------------
      String#unpack1     18.636M (± 1.6%) i/s -     93.420M in   5.014398s
    String#unpack[0]     18.537M (± 0.9%) i/s -     92.670M in   4.999732s

Comparison:
      String#unpack1: 18635760.6 i/s
    String#unpack[0]: 18536663.2 i/s - same-ish: difference falls within error

$ ruby -v code/time/iso8601-vs-parse.rb
truffleruby 21.1.0-dev-8deb9b1f, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601    21.510k i/100ms
          Time.parse     2.092k i/100ms
Calculating -------------------------------------
        Time.iso8601    276.968k (± 1.5%) i/s -      1.398M in   5.049301s
          Time.parse     26.315k (± 0.8%) i/s -    131.796k in   5.008801s

Comparison:
        Time.iso8601:   276967.5 i/s
          Time.parse:    26314.5 i/s - 10.53x  (± 0.00) slower

bundle exec rake  1646.13s user 32.48s system 134% cpu 20:52.39 total

```



## License

![CC-BY-SA](CC-BY-SA.png)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Code License

### CC0 1.0 Universal

To the extent possible under law, @JuanitoFatas has waived all copyright and related or neighboring rights to "fast-ruby".

This work belongs to the community.
