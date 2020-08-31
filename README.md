## Fast Truffle Ruby 


The idia of this project is to run all collected examples from the [Fast Ruby] (https://github.com/JuanitoFatas/fast-ruby) and run it against the latest truffle ruby version to see if the same results hold for the Truffle ruby. 

As you will see in the resalst below some results a quite different

## Results
```
$ ruby -v code/general/array-argument-vs-splat-arguments.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       219.202M i/100ms
Function with splat arguments
                         1.432k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          2.112B (± 4.3%) i/s -     10.741B in   5.095440s
Function with splat arguments
                         13.816k (± 4.7%) i/s -     70.168k in   5.090916s

Comparison:
Function with single Array argument: 2112088692.3 i/s
Function with splat arguments:    13815.7 i/s - 152876.21x  (± 0.00) slower

$ ruby -v code/general/assignment.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   220.271M i/100ms
Sequential Assignment
                       216.589M i/100ms
Calculating -------------------------------------
 Parallel Assignment      2.138B (± 3.0%) i/s -     10.793B in   5.053267s
Sequential Assignment
                          2.082B (± 5.7%) i/s -     10.396B in   5.009991s

Comparison:
 Parallel Assignment: 2137831220.1 i/s
Sequential Assignment: 2082185904.3 i/s - same-ish: difference falls within error

$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   216.333M i/100ms
       attr_accessor   219.477M i/100ms
Calculating -------------------------------------
   getter_and_setter      2.121B (± 3.3%) i/s -     10.600B in   5.002864s
       attr_accessor      2.147B (± 3.9%) i/s -     10.754B in   5.017349s

Comparison:
       attr_accessor: 2147065259.7 i/s
   getter_and_setter: 2121361025.4 i/s - same-ish: difference falls within error

$ ruby -v code/general/begin-rescue-vs-respond-to.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     7.667k i/100ms
         respond_to?   217.369M i/100ms
Calculating -------------------------------------
      begin...rescue     93.961k (± 4.3%) i/s -    475.354k in   5.069000s
         respond_to?      2.171B (± 2.5%) i/s -     10.868B in   5.008662s

Comparison:
         respond_to?: 2171346997.2 i/s
      begin...rescue:    93961.1 i/s - 23109.00x  (± 0.00) slower

$ ruby -v code/general/block-apply-method.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   216.921M i/100ms
             &method   218.258M i/100ms
Calculating -------------------------------------
              normal      2.157B (± 2.3%) i/s -     10.846B in   5.031524s
             &method      2.143B (± 3.0%) i/s -     10.913B in   5.096336s

Comparison:
              normal: 2156799591.2 i/s
             &method: 2143320369.5 i/s - same-ish: difference falls within error

$ ruby -v code/general/define_method-vs-module-eval.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                        76.000  i/100ms
       define_method    79.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.043k (±32.6%) i/s -      4.560k in   5.775666s
       define_method      3.143k (±29.6%) i/s -     11.771k in   5.010888s

Comparison:
       define_method:     3142.6 i/s
module_eval with string:     1042.7 i/s - 3.01x  (± 0.00) slower

$ ruby -v code/general/format-vs-round-and-to-s.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    61.545k i/100ms
       Kernel#format    76.700k i/100ms
            String#%    76.828k i/100ms
Calculating -------------------------------------
         Float#round    611.732k (± 3.3%) i/s -      3.077M in   5.036522s
       Kernel#format    764.998k (± 3.4%) i/s -      3.835M in   5.019227s
            String#%    763.813k (± 4.6%) i/s -      3.841M in   5.041008s

Comparison:
       Kernel#format:   764998.3 i/s
            String#%:   763813.4 i/s - same-ish: difference falls within error
         Float#round:   611731.9 i/s - 1.25x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct-on-access.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   221.973M i/100ms
          OpenStruct   324.149M i/100ms
Calculating -------------------------------------
                Hash      2.081B (± 4.9%) i/s -     10.433B in   5.026206s
          OpenStruct      3.409B (± 3.7%) i/s -     17.180B in   5.047493s

Comparison:
          OpenStruct: 3408553954.6 i/s
                Hash: 2081002286.5 i/s - 1.64x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   217.362M i/100ms
          OpenStruct   218.179M i/100ms
Calculating -------------------------------------
                Hash      2.149B (± 3.8%) i/s -     10.868B in   5.064294s
          OpenStruct      2.141B (± 3.4%) i/s -     10.909B in   5.101913s

Comparison:
                Hash: 2149439905.8 i/s
          OpenStruct: 2140796726.5 i/s - same-ish: difference falls within error

$ ruby -v code/general/inheritance-check.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal     1.310M i/100ms
  ancestors.include?   178.084k i/100ms
Calculating -------------------------------------
  less than or equal     13.319M (± 3.5%) i/s -     66.827M in   5.024031s
  ancestors.include?      1.692M (± 6.5%) i/s -      8.548M in   5.076513s

Comparison:
  less than or equal: 13318742.5 i/s
  ancestors.include?:  1691553.3 i/s - 7.87x  (± 0.00) slower

$ ruby -v code/general/loop-vs-while-true.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     3.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     34.234  (± 2.9%) i/s -    171.000  in   5.002620s
         Kernel loop      8.848  (± 0.0%) i/s -     45.000  in   5.090804s

Comparison:
          While Loop:       34.2 i/s
         Kernel loop:        8.8 i/s - 3.87x  (± 0.00) slower

$ ruby -v code/general/raise-vs-e2mmap.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Ruby exception: E2MM#Raise
                       375.000  i/100ms
Ruby exception: Kernel#raise
                       214.915M i/100ms
Calculating -------------------------------------
Ruby exception: E2MM#Raise
                          9.339k (± 5.1%) i/s -     46.875k in   5.033650s
Ruby exception: Kernel#raise
                          2.137B (± 3.9%) i/s -     10.746B in   5.037511s

Comparison:
Ruby exception: Kernel#raise: 2136604886.9 i/s
Ruby exception: E2MM#Raise:     9339.1 i/s - 228779.63x  (± 0.00) slower

Warming up --------------------------------------
Custom exception: E2MM#Raise
                       379.000  i/100ms
Custom exception: Kernel#raise
                       216.501M i/100ms
Calculating -------------------------------------
Custom exception: E2MM#Raise
                          9.556k (± 5.1%) i/s -     47.754k in   5.010979s
Custom exception: Kernel#raise
                          2.119B (± 4.4%) i/s -     10.609B in   5.015917s

Comparison:
Custom exception: Kernel#raise: 2119403777.2 i/s
Custom exception: E2MM#Raise:     9556.4 i/s - 221777.33x  (± 0.00) slower

$ ruby -v code/array/array-first-vs-index.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   207.849M i/100ms
         Array#first   210.978M i/100ms
Calculating -------------------------------------
           Array#[0]      2.149B (± 2.9%) i/s -     10.808B in   5.033679s
         Array#first      2.158B (± 2.8%) i/s -     10.971B in   5.088732s

Comparison:
         Array#first: 2157692594.9 i/s
           Array#[0]: 2149098369.0 i/s - same-ish: difference falls within error

$ ruby -v code/array/array-last-vs-index.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   330.188M i/100ms
          Array#last   351.070M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.425B (± 3.7%) i/s -     17.170B in   5.020424s
          Array#last      3.384B (± 3.3%) i/s -     17.202B in   5.089342s

Comparison:
          Array#[-1]: 3424999618.6 i/s
          Array#last: 3383927774.4 i/s - same-ish: difference falls within error

$ ruby -v code/array/bsearch-vs-find.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   346.447k i/100ms
Calculating -------------------------------------
                find      0.099  (± 0.0%) i/s -      1.000  in  10.128610s
             bsearch      3.292M (±10.8%) i/s -     16.283M in   5.069872s

Comparison:
             bsearch:  3292339.7 i/s
                find:        0.1 i/s - 33346826.21x  (± 0.00) slower

$ ruby -v code/array/insert-vs-unshift.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.167  (± 0.0%) i/s -      1.000  in   6.001039s
        Array#insert      0.309  (± 0.0%) i/s -      2.000  in   6.475371s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.85x  (± 0.00) slower

$ ruby -v code/array/length-vs-size-vs-count.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   335.757M i/100ms
          Array#size   349.062M i/100ms
         Array#count   352.353M i/100ms
Calculating -------------------------------------
        Array#length      3.455B (± 2.4%) i/s -     17.459B in   5.055893s
          Array#size      3.431B (± 3.1%) i/s -     17.453B in   5.091796s
         Array#count      3.435B (± 3.5%) i/s -     17.265B in   5.032068s

Comparison:
        Array#length: 3455264692.0 i/s
         Array#count: 3435449002.3 i/s - same-ish: difference falls within error
          Array#size: 3431152857.2 i/s - same-ish: difference falls within error

$ ruby -v code/array/shuffle-first-vs-sample.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    13.921k i/100ms
        Array#sample     1.420M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    137.367k (± 7.1%) i/s -    682.129k in   5.006137s
        Array#sample     14.684M (± 3.6%) i/s -     73.855M in   5.036481s

Comparison:
        Array#sample: 14683591.9 i/s
 Array#shuffle.first:   137366.6 i/s - 106.89x  (± 0.00) slower

$ ruby -v code/date/iso8601-vs-parse.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601   429.000  i/100ms
          Date.parse   588.000  i/100ms
Calculating -------------------------------------
        Date.iso8601     43.082k (±21.7%) i/s -    188.331k in   5.002481s
          Date.parse     47.198k (± 7.7%) i/s -    234.612k in   5.006664s

Comparison:
          Date.parse:    47197.9 i/s
        Date.iso8601:    43081.5 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/each-push-vs-map.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   291.087k i/100ms
           Array#map     1.049M i/100ms
Calculating -------------------------------------
   Array#each + push      2.841M (± 4.0%) i/s -     14.263M in   5.028479s
           Array#map     10.198M (± 2.8%) i/s -     51.419M in   5.046070s

Comparison:
           Array#map: 10197986.8 i/s
   Array#each + push:  2841295.1 i/s - 3.59x  (± 0.00) slower

$ ruby -v code/enumerable/each-vs-for-loop.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop   787.299k i/100ms
               #each   946.897k i/100ms
Calculating -------------------------------------
            For loop      7.799M (± 3.5%) i/s -     39.365M in   5.053818s
               #each      9.624M (± 4.3%) i/s -     48.292M in   5.028184s

Comparison:
               #each:  9624452.2 i/s
            For loop:  7798909.6 i/s - 1.23x  (± 0.00) slower

$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   375.260k i/100ms
     each_with_index   798.873k i/100ms
Calculating -------------------------------------
          While Loop      3.758M (± 3.7%) i/s -     18.763M in   5.000016s
     each_with_index      7.738M (± 4.8%) i/s -     39.145M in   5.071634s

Comparison:
     each_with_index:  7737870.5 i/s
          While Loop:  3758318.4 i/s - 2.06x  (± 0.00) slower

$ ruby -v code/enumerable/inject-symbol-vs-block.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   213.749k i/100ms
      inject to_proc   216.174k i/100ms
        inject block   211.548k i/100ms
Calculating -------------------------------------
       inject symbol      2.104M (± 4.2%) i/s -     10.687M in   5.088209s
      inject to_proc      2.119M (± 3.0%) i/s -     10.593M in   5.004136s
        inject block      2.116M (± 3.0%) i/s -     10.789M in   5.102494s

Comparison:
      inject to_proc:  2118728.3 i/s
        inject block:  2116365.0 i/s - same-ish: difference falls within error
       inject symbol:  2104442.8 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    29.066k i/100ms
   Array#map.flatten    17.334k i/100ms
      Array#flat_map    52.328k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    290.661k (± 3.7%) i/s -      1.453M in   5.007275s
   Array#map.flatten    174.717k (± 3.4%) i/s -    884.034k in   5.066197s
      Array#flat_map    531.937k (± 4.2%) i/s -      2.669M in   5.026501s

Comparison:
      Array#flat_map:   531937.0 i/s
Array#map.flatten(1):   290661.5 i/s - 1.83x  (± 0.00) slower
   Array#map.flatten:   174717.3 i/s - 3.04x  (± 0.00) slower

$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   208.856k i/100ms
  Array#reverse_each   521.461k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.084M (± 2.5%) i/s -     10.443M in   5.014612s
  Array#reverse_each      5.088M (± 3.2%) i/s -     25.552M in   5.027567s

Comparison:
  Array#reverse_each:  5087742.8 i/s
  Array#reverse.each:  2083847.1 i/s - 2.44x  (± 0.00) slower

$ ruby -v code/enumerable/select-first-vs-detect.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       496.110k i/100ms
   Enumerable#detect     5.138M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          5.076M (± 3.5%) i/s -    101.703M in  20.062851s
   Enumerable#detect     49.982M (± 3.9%) i/s -      1.002B in  20.078616s

Comparison:
   Enumerable#detect: 49981602.4 i/s
Enumerable#select.first:  5075978.4 i/s - 9.85x  (± 0.00) slower

$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       237.757k i/100ms
Enumerable#select.last
                       290.954k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.344M (± 3.1%) i/s -     11.888M in   5.076641s
Enumerable#select.last
                          3.010M (± 3.4%) i/s -     15.130M in   5.033073s

Comparison:
Enumerable#select.last:  3009683.9 i/s
Enumerable#reverse.detect:  2344060.7 i/s - 1.28x  (± 0.00) slower

$ ruby -v code/enumerable/sort-vs-sort_by.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         5.872k i/100ms
  Enumerable#sort_by     3.933k i/100ms
     Enumerable#sort     6.299k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         57.164k (±14.1%) i/s -    258.368k in   5.105317s
  Enumerable#sort_by     44.050k (±19.7%) i/s -    176.985k in   5.049411s
     Enumerable#sort     75.637k (± 3.5%) i/s -    377.940k in   5.003061s

Comparison:
     Enumerable#sort:    75637.3 i/s
Enumerable#sort_by (Symbol#to_proc):    57164.1 i/s - 1.32x  (± 0.00) slower
  Enumerable#sort_by:    44049.8 i/s - 1.72x  (± 0.00) slower

$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   288.858k i/100ms
Enumerable#sort_by...first
                        10.782k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      2.937M (± 3.5%) i/s -     14.732M in   5.023280s
Enumerable#sort_by...first
                        124.151k (± 4.0%) i/s -    625.356k in   5.045626s

Comparison:
   Enumerable#min_by:  2936558.2 i/s
Enumerable#sort_by...first:   124151.5 i/s - 23.65x  (± 0.00) slower

$ ruby -v code/hash/bracket-vs-dup.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   577.523k i/100ms
            Hash#dup   564.704k i/100ms
Calculating -------------------------------------
              Hash[]      5.577M (± 8.5%) i/s -     27.721M in   5.040237s
            Hash#dup      5.686M (± 3.7%) i/s -     28.800M in   5.072548s

Comparison:
            Hash#dup:  5685910.1 i/s
              Hash[]:  5577324.4 i/s - same-ish: difference falls within error

$ ruby -v code/hash/bracket-vs-fetch.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   343.017M i/100ms
  Hash#fetch, symbol   216.684M i/100ms
     Hash#[], string    12.254M i/100ms
  Hash#fetch, string    10.594M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      3.452B (± 3.2%) i/s -     17.494B in   5.072724s
  Hash#fetch, symbol      2.147B (± 3.3%) i/s -     10.834B in   5.052387s
     Hash#[], string    120.174M (± 2.6%) i/s -    600.429M in   4.999785s
  Hash#fetch, string    109.397M (± 3.1%) i/s -    550.906M in   5.040945s

Comparison:
     Hash#[], symbol: 3452217157.3 i/s
  Hash#fetch, symbol: 2146881129.0 i/s - 1.61x  (± 0.00) slower
     Hash#[], string: 120174176.0 i/s - 28.73x  (± 0.00) slower
  Hash#fetch, string: 109396550.0 i/s - 31.56x  (± 0.00) slower

$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig   919.069k i/100ms
             Hash#[]     5.196M i/100ms
          Hash#[] ||     5.078M i/100ms
          Hash#[] &&     5.279M i/100ms
          Hash#fetch     5.269M i/100ms
 Hash#fetch fallback     5.098M i/100ms
Calculating -------------------------------------
            Hash#dig      9.855M (± 2.9%) i/s -     49.630M in   5.040385s
             Hash#[]     51.333M (± 4.3%) i/s -    259.801M in   5.071396s
          Hash#[] ||     51.533M (± 3.4%) i/s -    258.989M in   5.031585s
          Hash#[] &&     51.554M (± 3.8%) i/s -    258.667M in   5.025212s
          Hash#fetch     51.924M (± 2.7%) i/s -    263.426M in   5.077306s
 Hash#fetch fallback     51.671M (± 3.1%) i/s -    260.022M in   5.037290s

Comparison:
          Hash#fetch: 51923500.6 i/s
 Hash#fetch fallback: 51670614.0 i/s - same-ish: difference falls within error
          Hash#[] &&: 51554339.7 i/s - same-ish: difference falls within error
          Hash#[] ||: 51533450.6 i/s - same-ish: difference falls within error
             Hash#[]: 51332846.4 i/s - same-ish: difference falls within error
            Hash#dig:  9855234.4 i/s - 5.27x  (± 0.00) slower

$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   348.389M i/100ms
  Hash#fetch + block   216.993M i/100ms
    Hash#fetch + arg   342.402M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      3.433B (± 3.5%) i/s -     17.419B in   5.080281s
  Hash#fetch + block      2.141B (± 3.6%) i/s -     10.850B in   5.075145s
    Hash#fetch + arg      3.437B (± 3.5%) i/s -     17.463B in   5.087024s

Comparison:
    Hash#fetch + arg: 3437328699.2 i/s
  Hash#fetch + const: 3433207010.5 i/s - same-ish: difference falls within error
  Hash#fetch + block: 2140697510.6 i/s - 1.61x  (± 0.00) slower

$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h     7.100k i/100ms
         sort + to_h     2.894k i/100ms
Calculating -------------------------------------
      sort_by + to_h    649.674k (±19.8%) i/s -      2.755M in   5.003919s
         sort + to_h     92.906k (± 5.3%) i/s -    463.040k in   4.999123s

Comparison:
      sort_by + to_h:   649673.8 i/s
         sort + to_h:    92906.0 i/s - 6.99x  (± 0.00) slower

$ ruby -v code/hash/keys-each-vs-each_key.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each     1.534M i/100ms
       Hash#each_key     4.096M i/100ms
Calculating -------------------------------------
      Hash#keys.each     15.233M (± 4.2%) i/s -     76.691M in   5.044040s
       Hash#each_key     40.588M (± 3.2%) i/s -    204.776M in   5.050609s

Comparison:
       Hash#each_key: 40588475.1 i/s
      Hash#keys.each: 15232967.5 i/s - 2.66x  (± 0.00) slower

$ ruby -v code/hash/keys-include-vs-key.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?    86.000  i/100ms
           Hash#key?     6.013M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      4.360k (±12.7%) i/s -     21.328k in   5.001103s
           Hash#key?     64.811M (± 3.1%) i/s -    324.676M in   5.014507s

Comparison:
           Hash#key?: 64811418.8 i/s
  Hash#keys.include?:     4360.4 i/s - 14863.74x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-[]=.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    57.969k i/100ms
            Hash#[]=    56.058k i/100ms
Calculating -------------------------------------
         Hash#merge!    570.224k (± 5.1%) i/s -      2.898M in   5.097187s
            Hash#[]=    542.173k (± 3.7%) i/s -      2.747M in   5.073356s

Comparison:
         Hash#merge!:   570224.1 i/s
            Hash#[]=:   542173.3 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                        23.640k i/100ms
      Hash#merge({})    13.461k i/100ms
 Hash#dup#merge!({})    28.894k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        261.790k (± 8.8%) i/s -      1.300M in   5.040033s
      Hash#merge({})    161.767k (± 8.3%) i/s -    807.660k in   5.066444s
 Hash#dup#merge!({})    281.326k (± 5.1%) i/s -      1.416M in   5.047408s

Comparison:
 Hash#dup#merge!({}):   281326.1 i/s
{}#merge!(Hash) do end:   261789.7 i/s - same-ish: difference falls within error
      Hash#merge({}):   161767.4 i/s - 1.74x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-double-splat-operator.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   213.137M i/100ms
          Hash#merge   216.117M i/100ms
Calculating -------------------------------------
        Hash#**other      2.158B (± 2.8%) i/s -     10.870B in   5.041326s
          Hash#merge      2.162B (± 3.2%) i/s -     10.806B in   5.004369s

Comparison:
          Hash#merge: 2161616030.1 i/s
        Hash#**other: 2158015879.9 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-vs-merge-bang.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge   720.000  i/100ms
         Hash#merge!    56.842k i/100ms
Calculating -------------------------------------
          Hash#merge      8.898k (± 4.3%) i/s -     44.640k in   5.026975s
         Hash#merge!    545.257k (± 4.4%) i/s -      2.728M in   5.014418s

Comparison:
         Hash#merge!:   545256.8 i/s
          Hash#merge:     8897.7 i/s - 61.28x  (± 0.00) slower

$ ruby -v code/hash/slice-native-vs-before-native.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice        1.982M i/100ms
Array#each               1.700M i/100ms
Array#each_w/_object     1.668M i/100ms
Hash#select-include      2.119M i/100ms
Calculating -------------------------------------
Hash#native-slice        20.063M (± 3.3%) i/s -    101.101M in   5.044754s
Array#each               16.600M (± 3.1%) i/s -     83.317M in   5.024333s
Array#each_w/_object     16.271M (± 4.5%) i/s -     81.728M in   5.034209s
Hash#select-include      20.871M (± 4.5%) i/s -    105.926M in   5.086603s

Comparison:
Hash#select-include : 20870937.9 i/s
Hash#native-slice   : 20063429.6 i/s - same-ish: difference falls within error
Array#each          : 16599660.9 i/s - 1.26x  (± 0.00) slower
Array#each_w/_object: 16271295.9 i/s - 1.28x  (± 0.00) slower

$ ruby -v code/hash/values-include-vs-value.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?    87.000  i/100ms
         Hash#value?     2.414k i/100ms
Calculating -------------------------------------
Hash#values.include?      4.343k (±12.1%) i/s -     21.315k in   5.006982s
         Hash#value?     23.909k (± 4.8%) i/s -    120.700k in   5.060296s

Comparison:
         Hash#value?:    23909.5 i/s
Hash#values.include?:     4343.1 i/s - 5.51x  (± 0.00) slower

$ ruby -v code/method/call-vs-send-vs-method_missing.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   220.841M i/100ms
                send   218.589M i/100ms
      method_missing   216.071M i/100ms
Calculating -------------------------------------
                call      2.140B (± 3.7%) i/s -     10.821B in   5.064305s
                send      2.113B (± 3.7%) i/s -     10.711B in   5.077085s
      method_missing      2.081B (± 6.3%) i/s -     10.371B in   5.004716s

Comparison:
                call: 2139971916.2 i/s
                send: 2112606604.5 i/s - same-ish: difference falls within error
      method_missing: 2081118483.9 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/block-vs-to_proc.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    67.722k i/100ms
      Symbol#to_proc    67.169k i/100ms
Calculating -------------------------------------
               Block    677.757k (± 8.3%) i/s -      3.386M in   5.061962s
      Symbol#to_proc    662.437k (± 9.0%) i/s -      3.291M in   5.044292s

Comparison:
               Block:   677756.6 i/s
      Symbol#to_proc:   662436.7 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   347.719M i/100ms
       block + yield   345.644M i/100ms
        unused block   344.491M i/100ms
               yield   350.683M i/100ms
Calculating -------------------------------------
          block.call      3.442B (± 3.5%) i/s -     17.386B in   5.057240s
       block + yield      3.450B (± 3.4%) i/s -     17.282B in   5.016046s
        unused block      3.456B (± 3.5%) i/s -     17.569B in   5.091131s
               yield      3.436B (± 3.8%) i/s -     17.183B in   5.008688s

Comparison:
        unused block: 3455635570.1 i/s
       block + yield: 3449595857.4 i/s - same-ish: difference falls within error
          block.call: 3442370947.3 i/s - same-ish: difference falls within error
               yield: 3435983729.8 i/s - same-ish: difference falls within error

$ ruby -v code/range/cover-vs-include.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?    60.698M i/100ms
      range#include?     8.385k i/100ms
       range#member?     7.949k i/100ms
       plain compare   350.184M i/100ms
Calculating -------------------------------------
        range#cover?      3.415B (±10.4%) i/s -     16.024B in   5.005423s
      range#include?    156.102k (± 4.5%) i/s -    779.805k in   5.005918s
       range#member?    157.924k (± 5.0%) i/s -    794.900k in   5.047057s
       plain compare      3.427B (± 3.9%) i/s -     17.159B in   5.014892s

Comparison:
       plain compare: 3427296440.8 i/s
        range#cover?: 3414686588.4 i/s - same-ish: difference falls within error
       range#member?:   157923.8 i/s - 21702.21x  (± 0.00) slower
      range#include?:   156102.3 i/s - 21955.46x  (± 0.00) slower

$ ruby -v code/string/===-vs-=~-vs-match.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     1.621M i/100ms
           String#=~     1.473M i/100ms
          Regexp#===     1.485M i/100ms
        String#match     1.266M i/100ms
Calculating -------------------------------------
       String#match?     16.022M (± 3.6%) i/s -     81.070M in   5.066651s
           String#=~     14.383M (± 3.4%) i/s -     72.201M in   5.025674s
          Regexp#===     14.215M (± 5.0%) i/s -     71.258M in   5.026482s
        String#match     12.514M (± 3.1%) i/s -     63.321M in   5.064964s

Comparison:
       String#match?: 16022491.1 i/s
           String#=~: 14383313.8 i/s - 1.11x  (± 0.00) slower
          Regexp#===: 14214978.4 i/s - 1.13x  (± 0.00) slower
        String#match: 12514162.4 i/s - 1.28x  (± 0.00) slower

$ ruby -v code/string/casecmp-vs-downcase-==.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.308M i/100ms
      String#casecmp     4.599M i/100ms
Calculating -------------------------------------
String#downcase + ==     22.840M (± 6.7%) i/s -    115.396M in   5.076133s
      String#casecmp     44.952M (± 3.0%) i/s -    225.360M in   5.018080s

Comparison:
      String#casecmp: 44951749.7 i/s
String#downcase + ==: 22840445.9 i/s - 1.97x  (± 0.00) slower

$ ruby -v code/string/concatenation.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   218.702M i/100ms
       String#concat   215.497M i/100ms
       String#append   220.165M i/100ms
         "foo" "bar"   220.415M i/100ms
  "#{'foo'}#{'bar'}"   221.184M i/100ms
Calculating -------------------------------------
            String#+      2.144B (± 3.3%) i/s -     10.716B in   5.004987s
       String#concat      2.163B (± 2.5%) i/s -     10.990B in   5.083436s
       String#append      2.152B (± 3.2%) i/s -     10.788B in   5.017661s
         "foo" "bar"      2.167B (± 2.8%) i/s -     11.021B in   5.090753s
  "#{'foo'}#{'bar'}"      2.152B (± 4.1%) i/s -     10.838B in   5.045402s

Comparison:
         "foo" "bar": 2166686324.6 i/s
       String#concat: 2163424454.3 i/s - same-ish: difference falls within error
       String#append: 2152356943.0 i/s - same-ish: difference falls within error
  "#{'foo'}#{'bar'}": 2151922056.7 i/s - same-ish: difference falls within error
            String#+: 2143557783.5 i/s - same-ish: difference falls within error

$ ruby -v code/string/dup-vs-unary-plus.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   337.730M i/100ms
          String#dup   217.375M i/100ms
Calculating -------------------------------------
           String#+@      3.429B (± 3.7%) i/s -     17.224B in   5.030209s
          String#dup      2.154B (± 3.4%) i/s -     10.869B in   5.052912s

Comparison:
           String#+@: 3429140562.2 i/s
          String#dup: 2153676070.8 i/s - 1.59x  (± 0.00) slower

$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   228.812k i/100ms
       String#match?   242.813k i/100ms
    String#end_with?     1.034M i/100ms
Calculating -------------------------------------
           String#=~      2.214M (± 4.5%) i/s -     11.212M in   5.074467s
       String#match?      2.371M (± 4.1%) i/s -     11.898M in   5.027333s
    String#end_with?     10.284M (± 3.2%) i/s -     51.685M in   5.030958s

Comparison:
    String#end_with?: 10284453.6 i/s
       String#match?:  2370914.5 i/s - 4.34x  (± 0.00) slower
           String#=~:  2214206.9 i/s - 4.64x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-sub.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub   107.958k i/100ms
          String#sub    92.601k i/100ms
String#dup["string"]=
                         8.842M i/100ms
Calculating -------------------------------------
         String#gsub      1.160M (± 4.3%) i/s -      5.830M in   5.035640s
          String#sub    900.135k (± 2.9%) i/s -      4.537M in   5.045275s
String#dup["string"]=
                         88.283M (± 4.3%) i/s -    442.104M in   5.017895s

Comparison:
String#dup["string"]=: 88283366.6 i/s
         String#gsub:  1160081.7 i/s - 76.10x  (± 0.00) slower
          String#sub:   900135.3 i/s - 98.08x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-tr.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub   135.349k i/100ms
           String#tr   264.165k i/100ms
Calculating -------------------------------------
         String#gsub      3.320M (± 4.0%) i/s -     16.648M in   5.023736s
           String#tr      2.646M (± 3.4%) i/s -     13.472M in   5.098086s

Comparison:
         String#gsub:  3319525.6 i/s
           String#tr:  2646077.1 i/s - 1.25x  (± 0.00) slower

$ ruby -v code/string/mutable_vs_immutable_strings.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze   205.876M i/100ms
         With Freeze   207.068M i/100ms
Calculating -------------------------------------
      Without Freeze      2.117B (± 4.7%) i/s -     10.706B in   5.069705s
         With Freeze      2.144B (± 3.5%) i/s -     10.768B in   5.027929s

Comparison:
         With Freeze: 2144384156.8 i/s
      Without Freeze: 2116617985.7 i/s - same-ish: difference falls within error

$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/     3.316k i/100ms
      String#squeeze    66.821k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     40.303k (± 4.0%) i/s -    202.276k in   5.027559s
      String#squeeze    659.722k (± 4.2%) i/s -      3.341M in   5.073881s

Comparison:
      String#squeeze:   659722.4 i/s
 String#gsub/regex+/:    40303.5 i/s - 16.37x  (± 0.00) slower

$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   767.786k i/100ms
       String#match?   962.997k i/100ms
  String#start_with?     2.844M i/100ms
Calculating -------------------------------------
           String#=~      7.571M (± 3.2%) i/s -     38.389M in   5.076380s
       String#match?      9.783M (± 3.7%) i/s -     49.113M in   5.027719s
  String#start_with?     28.078M (± 3.5%) i/s -    142.181M in   5.070645s

Comparison:
  String#start_with?: 28078258.7 i/s
       String#match?:  9782530.4 i/s - 2.87x  (± 0.00) slower
           String#=~:  7570569.4 i/s - 3.71x  (± 0.00) slower

$ ruby -v code/string/start_with-vs-substring-==.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?   439.105k i/100ms
    String#[0, n] ==   396.200k i/100ms
   String#[RANGE] ==    22.263k i/100ms
   String#[0...n] ==   301.914k i/100ms
Calculating -------------------------------------
  String#start_with?      4.453M (± 4.3%) i/s -     22.394M in   5.039365s
    String#[0, n] ==      3.885M (± 6.2%) i/s -     19.414M in   5.023732s
   String#[RANGE] ==      4.104M (± 9.6%) i/s -     20.282M in   4.998171s
   String#[0...n] ==      2.964M (± 2.8%) i/s -     15.096M in   5.096903s

Comparison:
  String#start_with?:  4453201.5 i/s
   String#[RANGE] ==:  4103969.1 i/s - same-ish: difference falls within error
    String#[0, n] ==:  3884653.4 i/s - 1.15x  (± 0.00) slower
   String#[0...n] ==:  2964193.2 i/s - 1.50x  (± 0.00) slower

$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=    10.089M i/100ms
 String#sub!'string'    95.351k i/100ms
String#gsub!'string'    77.389k i/100ms
  String#[/regexp/]=   473.342k i/100ms
 String#sub!/regexp/   748.849k i/100ms
String#gsub!/regexp/   109.296k i/100ms
Calculating -------------------------------------
  String#['string']=     98.491M (± 9.5%) i/s -    484.254M in   5.005087s
 String#sub!'string'    916.234k (± 4.8%) i/s -      4.577M in   5.007371s
String#gsub!'string'      1.144M (± 4.3%) i/s -      5.727M in   5.015907s
  String#[/regexp/]=      4.701M (± 3.7%) i/s -     23.667M in   5.041398s
 String#sub!/regexp/      7.238M (± 3.4%) i/s -     36.694M in   5.075583s
String#gsub!/regexp/      2.829M (± 5.8%) i/s -     14.099M in   5.003071s

Comparison:
  String#['string']=: 98490996.9 i/s
 String#sub!/regexp/:  7238059.4 i/s - 13.61x  (± 0.00) slower
  String#[/regexp/]=:  4701305.9 i/s - 20.95x  (± 0.00) slower
String#gsub!/regexp/:  2828628.2 i/s - 34.82x  (± 0.00) slower
String#gsub!'string':  1143999.6 i/s - 86.09x  (± 0.00) slower
 String#sub!'string':   916234.2 i/s - 107.50x  (± 0.00) slower

$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub   623.588k i/100ms
        String#chomp     2.432M i/100ms
String#delete_suffix     2.496M i/100ms
Calculating -------------------------------------
          String#sub      6.440M (± 3.4%) i/s -     32.427M in   5.041727s
        String#chomp     24.677M (± 3.0%) i/s -    124.026M in   5.030456s
String#delete_suffix     24.964M (± 4.6%) i/s -    124.813M in   5.011012s

Comparison:
String#delete_suffix: 24963981.3 i/s
        String#chomp: 24677491.2 i/s - same-ish: difference falls within error
          String#sub:  6439597.3 i/s - 3.88x  (± 0.00) slower

$ ruby -v code/string/sub-vs-delete_prefix.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     2.748M i/100ms
          String#sub   722.766k i/100ms
Calculating -------------------------------------
String#delete_prefix     27.163M (± 3.9%) i/s -    137.419M in   5.067258s
          String#sub      7.358M (± 2.9%) i/s -     36.861M in   5.014284s

Comparison:
String#delete_prefix: 27162850.3 i/s
          String#sub:  7357522.4 i/s - 3.69x  (± 0.00) slower

$ ruby -v code/string/unpack1-vs-unpack[0].rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     2.197M i/100ms
    String#unpack[0]     2.254M i/100ms
Calculating -------------------------------------
      String#unpack1     22.452M (± 3.2%) i/s -    114.234M in   5.093299s
    String#unpack[0]     22.169M (± 4.7%) i/s -    112.689M in   5.095354s

Comparison:
      String#unpack1: 22452385.4 i/s
    String#unpack[0]: 22168985.3 i/s - same-ish: difference falls within error

$ ruby -v code/time/iso8601-vs-parse.rb
truffleruby 20.3.0-dev-06662f0c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601     2.743k i/100ms
          Time.parse   430.000  i/100ms
Calculating -------------------------------------
        Time.iso8601    282.389k (±14.9%) i/s -      1.355M in   5.001348s
          Time.parse     41.846k (±10.2%) i/s -    205.540k in   5.002878s

Comparison:
        Time.iso8601:   282388.8 i/s
          Time.parse:    41845.8 i/s - 6.75x  (± 0.00) slower



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
