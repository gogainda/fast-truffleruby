## Fast Truffle Ruby 


The idia of this project is to run all collected examples from the [Fast Ruby] (https://github.com/JuanitoFatas/fast-ruby) and run it against the latest truffle ruby version to see if the same results hold for the Truffle ruby. 

As you will see in the resalst below some results a quite different
1773.87s user 39.75s system 141% cpu 21:18.57 total
## Results
```
$ ruby -v code/general/array-argument-vs-splat-arguments.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       329.467M i/100ms
Function with splat arguments
                         1.580k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          3.358B (± 3.8%) i/s -     16.803B in   5.011609s
Function with splat arguments
                         15.593k (± 3.7%) i/s -     79.000k in   5.074108s

Comparison:
Function with single Array argument: 3358123185.8 i/s
Function with splat arguments:    15592.8 i/s - 215363.96x  (± 0.00) slower

$ ruby -v code/general/assignment.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   333.993M i/100ms
Sequential Assignment
                       336.264M i/100ms
Calculating -------------------------------------
 Parallel Assignment      3.358B (± 3.2%) i/s -     17.034B in   5.078556s
Sequential Assignment
                          3.364B (± 3.6%) i/s -     16.813B in   5.005675s

Comparison:
Sequential Assignment: 3363735817.0 i/s
 Parallel Assignment: 3357797282.2 i/s - same-ish: difference falls within error

$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   323.022M i/100ms
       attr_accessor   335.827M i/100ms
Calculating -------------------------------------
   getter_and_setter      3.364B (± 3.7%) i/s -     16.797B in   5.001502s
       attr_accessor      3.350B (± 3.8%) i/s -     16.791B in   5.020222s

Comparison:
   getter_and_setter: 3363666585.0 i/s
       attr_accessor: 3350130642.8 i/s - same-ish: difference falls within error

$ ruby -v code/general/begin-rescue-vs-respond-to.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     6.929k i/100ms
         respond_to?   324.294M i/100ms
Calculating -------------------------------------
      begin...rescue     87.790k (± 4.4%) i/s -    443.456k in   5.062107s
         respond_to?      3.353B (± 3.9%) i/s -     16.863B in   5.037955s

Comparison:
         respond_to?: 3353050222.8 i/s
      begin...rescue:    87789.9 i/s - 38194.02x  (± 0.00) slower

$ ruby -v code/general/block-apply-method.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   332.926M i/100ms
             &method   327.122M i/100ms
Calculating -------------------------------------
              normal      3.338B (± 4.7%) i/s -     16.646B in   4.999558s
             &method      3.355B (± 3.6%) i/s -     17.010B in   5.077267s

Comparison:
             &method: 3355005689.0 i/s
              normal: 3337618688.4 i/s - same-ish: difference falls within error

$ ruby -v code/general/define_method-vs-module-eval.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                        27.000  i/100ms
       define_method   336.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.307k (±36.2%) i/s -      4.644k in   5.222634s
       define_method      2.563k (±29.5%) i/s -     12.096k in   5.128277s

Comparison:
       define_method:     2562.8 i/s
module_eval with string:     1307.3 i/s - 1.96x  (± 0.00) slower

$ ruby -v code/general/format-vs-round-and-to-s.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    45.971k i/100ms
       Kernel#format    83.453k i/100ms
            String#%    82.829k i/100ms
Calculating -------------------------------------
         Float#round    626.237k (± 4.8%) i/s -      3.126M in   5.004524s
       Kernel#format    826.133k (± 3.8%) i/s -      4.173M in   5.058873s
            String#%    829.269k (± 3.5%) i/s -      4.141M in   5.001019s

Comparison:
            String#%:   829268.8 i/s
       Kernel#format:   826133.3 i/s - same-ish: difference falls within error
         Float#round:   626236.7 i/s - 1.32x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct-on-access.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   209.202M i/100ms
          OpenStruct    70.557M i/100ms
Calculating -------------------------------------
                Hash      2.102B (± 3.4%) i/s -     10.669B in   5.081962s
          OpenStruct    693.398M (± 3.9%) i/s -      3.528B in   5.096094s

Comparison:
                Hash: 2102035281.0 i/s
          OpenStruct: 693398475.3 i/s - 3.03x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   332.025M i/100ms
          OpenStruct   309.522M i/100ms
Calculating -------------------------------------
                Hash      3.345B (± 3.9%) i/s -     16.933B in   5.070705s
          OpenStruct      3.315B (± 4.4%) i/s -     16.714B in   5.052261s

Comparison:
                Hash: 3344998082.5 i/s
          OpenStruct: 3315158492.5 i/s - same-ish: difference falls within error

$ ruby -v code/general/inheritance-check.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal   907.064k i/100ms
  ancestors.include?   179.228k i/100ms
Calculating -------------------------------------
  less than or equal     13.238M (± 4.4%) i/s -     66.216M in   5.012553s
  ancestors.include?      1.770M (± 3.9%) i/s -      8.961M in   5.070498s

Comparison:
  less than or equal: 13237684.6 i/s
  ancestors.include?:  1770316.4 i/s - 7.48x  (± 0.00) slower

$ ruby -v code/general/loop-vs-while-true.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     1.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     33.548  (± 3.0%) i/s -    168.000  in   5.018850s
         Kernel loop      8.583  (± 0.0%) i/s -     43.000  in   5.016245s

Comparison:
          While Loop:       33.5 i/s
         Kernel loop:        8.6 i/s - 3.91x  (± 0.00) slower

$ ruby -v code/general/raise-vs-e2mmap.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
$ ruby -v code/array/array-first-vs-index.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   208.021M i/100ms
         Array#first   211.895M i/100ms
Calculating -------------------------------------
           Array#[0]      2.083B (± 3.5%) i/s -     10.609B in   5.101072s
         Array#first      2.098B (± 3.4%) i/s -     10.595B in   5.055646s

Comparison:
         Array#first: 2098268179.0 i/s
           Array#[0]: 2082579588.4 i/s - same-ish: difference falls within error

$ ruby -v code/array/array-last-vs-index.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   329.808M i/100ms
          Array#last   333.331M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.344B (± 3.6%) i/s -     16.820B in   5.037415s
          Array#last      3.347B (± 3.2%) i/s -     17.000B in   5.084758s

Comparison:
          Array#last: 3347156556.4 i/s
          Array#[-1]: 3343723658.1 i/s - same-ish: difference falls within error

$ ruby -v code/array/bsearch-vs-find.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   360.214k i/100ms
Calculating -------------------------------------
                find      0.108  (± 0.0%) i/s -      1.000  in   9.248729s
             bsearch      3.585M (±10.2%) i/s -     17.650M in   5.003322s

Comparison:
             bsearch:  3584883.9 i/s
                find:        0.1 i/s - 33155618.33x  (± 0.00) slower

$ ruby -v code/array/insert-vs-unshift.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.163  (± 0.0%) i/s -      1.000  in   6.134688s
        Array#insert      0.300  (± 0.0%) i/s -      2.000  in   6.673390s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.84x  (± 0.00) slower

$ ruby -v code/array/length-vs-size-vs-count.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   213.111M i/100ms
          Array#size   209.148M i/100ms
         Array#count   210.205M i/100ms
Calculating -------------------------------------
        Array#length      2.097B (± 3.4%) i/s -     10.656B in   5.086873s
          Array#size      2.094B (± 3.5%) i/s -     10.457B in   5.001512s
         Array#count      2.076B (± 4.3%) i/s -     10.510B in   5.072320s

Comparison:
        Array#length: 2097361062.5 i/s
          Array#size: 2093701248.9 i/s - same-ish: difference falls within error
         Array#count: 2076156845.9 i/s - same-ish: difference falls within error

$ ruby -v code/array/shuffle-first-vs-sample.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    14.233k i/100ms
        Array#sample     1.480M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    139.077k (± 7.1%) i/s -    697.417k in   5.052065s
        Array#sample     15.436M (± 4.5%) i/s -     78.433M in   5.092689s

Comparison:
        Array#sample: 15435562.2 i/s
 Array#shuffle.first:   139077.4 i/s - 110.99x  (± 0.00) slower

$ ruby -v code/date/iso8601-vs-parse.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601   439.000  i/100ms
          Date.parse   695.000  i/100ms
Calculating -------------------------------------
        Date.iso8601     39.073k (±14.9%) i/s -    189.209k in   5.001238s
          Date.parse     40.669k (± 6.4%) i/s -    202.940k in   5.012885s

Comparison:
          Date.parse:    40669.2 i/s
        Date.iso8601:    39072.6 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/each-push-vs-map.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   310.017k i/100ms
           Array#map     1.193M i/100ms
Calculating -------------------------------------
   Array#each + push      3.116M (± 3.7%) i/s -     15.811M in   5.081681s
           Array#map     12.831M (± 4.6%) i/s -     64.400M in   5.030385s

Comparison:
           Array#map: 12831425.4 i/s
   Array#each + push:  3115829.3 i/s - 4.12x  (± 0.00) slower

$ ruby -v code/enumerable/each-vs-for-loop.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop   873.971k i/100ms
               #each     1.129M i/100ms
Calculating -------------------------------------
            For loop      8.958M (± 3.0%) i/s -     45.446M in   5.078092s
               #each     12.112M (± 4.0%) i/s -     60.941M in   5.040120s

Comparison:
               #each: 12112124.7 i/s
            For loop:  8958418.1 i/s - 1.35x  (± 0.00) slower

$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   396.555k i/100ms
     each_with_index     1.116M i/100ms
Calculating -------------------------------------
          While Loop      4.027M (± 3.1%) i/s -     20.224M in   5.027819s
     each_with_index     11.823M (± 4.6%) i/s -     59.163M in   5.015592s

Comparison:
     each_with_index: 11823214.0 i/s
          While Loop:  4026770.9 i/s - 2.94x  (± 0.00) slower

$ ruby -v code/enumerable/inject-symbol-vs-block.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   191.359k i/100ms
      inject to_proc   207.415k i/100ms
        inject block   209.456k i/100ms
Calculating -------------------------------------
       inject symbol      2.048M (± 3.7%) i/s -     10.333M in   5.053940s
      inject to_proc      2.055M (± 3.5%) i/s -     10.371M in   5.052196s
        inject block      2.040M (± 5.0%) i/s -     10.263M in   5.044725s

Comparison:
      inject to_proc:  2055412.2 i/s
       inject symbol:  2047695.4 i/s - same-ish: difference falls within error
        inject block:  2040351.8 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    21.654k i/100ms
   Array#map.flatten    21.384k i/100ms
      Array#flat_map    53.982k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    215.914k (± 3.4%) i/s -      1.083M in   5.020768s
   Array#map.flatten    225.823k (± 3.7%) i/s -      1.133M in   5.026381s
      Array#flat_map    574.238k (± 3.9%) i/s -      2.915M in   5.084524s

Comparison:
      Array#flat_map:   574237.6 i/s
   Array#map.flatten:   225823.3 i/s - 2.54x  (± 0.00) slower
Array#map.flatten(1):   215914.0 i/s - 2.66x  (± 0.00) slower

$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   199.125k i/100ms
  Array#reverse_each   498.821k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.790M (± 4.1%) i/s -     14.138M in   5.076428s
  Array#reverse_each      4.937M (± 3.7%) i/s -     24.941M in   5.059735s

Comparison:
  Array#reverse_each:  4936567.8 i/s
  Array#reverse.each:  2790048.1 i/s - 1.77x  (± 0.00) slower

$ ruby -v code/enumerable/select-first-vs-detect.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       503.620k i/100ms
   Enumerable#detect     4.741M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          6.379M (± 5.2%) i/s -    127.416M in  20.050670s
   Enumerable#detect     49.343M (± 3.7%) i/s -    986.035M in  20.013029s

Comparison:
   Enumerable#detect: 49343124.0 i/s
Enumerable#select.first:  6378956.9 i/s - 7.74x  (± 0.00) slower

$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       276.171k i/100ms
Enumerable#select.last
                       445.363k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.731M (± 4.4%) i/s -     13.809M in   5.066495s
Enumerable#select.last
                          4.450M (± 3.8%) i/s -     22.268M in   5.011528s

Comparison:
Enumerable#select.last:  4450353.5 i/s
Enumerable#reverse.detect:  2731259.0 i/s - 1.63x  (± 0.00) slower

$ ruby -v code/enumerable/sort-vs-sort_by.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         2.212k i/100ms
  Enumerable#sort_by     3.273k i/100ms
     Enumerable#sort     1.721k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         52.161k (±20.4%) i/s -    227.836k in   5.009219s
  Enumerable#sort_by     52.764k (±20.1%) i/s -    232.383k in   5.018231s
     Enumerable#sort     71.553k (± 4.9%) i/s -    357.968k in   5.016267s

Comparison:
     Enumerable#sort:    71552.6 i/s
  Enumerable#sort_by:    52764.0 i/s - 1.36x  (± 0.00) slower
Enumerable#sort_by (Symbol#to_proc):    52160.6 i/s - 1.37x  (± 0.00) slower

$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   357.323k i/100ms
Enumerable#sort_by...first
                         6.886k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      3.558M (± 4.0%) i/s -     17.866M in   5.030630s
Enumerable#sort_by...first
                        111.108k (± 4.0%) i/s -    557.766k in   5.028944s

Comparison:
   Enumerable#min_by:  3557792.5 i/s
Enumerable#sort_by...first:   111108.0 i/s - 32.02x  (± 0.00) slower

$ ruby -v code/hash/bracket-vs-dup.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   618.820k i/100ms
            Hash#dup   617.121k i/100ms
Calculating -------------------------------------
              Hash[]      6.084M (± 7.0%) i/s -     30.322M in   5.022616s
            Hash#dup      6.019M (± 9.5%) i/s -     30.239M in   5.098073s

Comparison:
              Hash[]:  6083852.6 i/s
            Hash#dup:  6019338.3 i/s - same-ish: difference falls within error

$ ruby -v code/hash/bracket-vs-fetch.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   332.302M i/100ms
  Hash#fetch, symbol   210.430M i/100ms
     Hash#[], string     8.526M i/100ms
  Hash#fetch, string     7.830M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      3.372B (± 3.3%) i/s -     16.947B in   5.032296s
  Hash#fetch, symbol      2.093B (± 4.3%) i/s -     10.522B in   5.036272s
     Hash#[], string     84.731M (± 3.5%) i/s -    426.299M in   5.038194s
  Hash#fetch, string     82.039M (± 3.4%) i/s -    414.964M in   5.064692s

Comparison:
     Hash#[], symbol: 3371842895.0 i/s
  Hash#fetch, symbol: 2093378747.8 i/s - 1.61x  (± 0.00) slower
     Hash#[], string: 84730586.9 i/s - 39.79x  (± 0.00) slower
  Hash#fetch, string: 82038616.4 i/s - 41.10x  (± 0.00) slower

$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig     1.037M i/100ms
             Hash#[]     5.558M i/100ms
          Hash#[] ||     5.482M i/100ms
          Hash#[] &&     5.467M i/100ms
          Hash#fetch     5.281M i/100ms
 Hash#fetch fallback     5.184M i/100ms
Calculating -------------------------------------
            Hash#dig      9.914M (± 3.4%) i/s -     49.777M in   5.026918s
             Hash#[]     53.218M (± 5.0%) i/s -    266.792M in   5.026458s
          Hash#[] ||     54.358M (± 3.6%) i/s -    274.107M in   5.049633s
          Hash#[] &&     54.348M (± 3.7%) i/s -    273.369M in   5.037753s
          Hash#fetch     52.392M (± 4.4%) i/s -    264.059M in   5.050505s
 Hash#fetch fallback     53.015M (± 4.0%) i/s -    269.577M in   5.093893s

Comparison:
          Hash#[] ||: 54358318.8 i/s
          Hash#[] &&: 54347757.6 i/s - same-ish: difference falls within error
             Hash#[]: 53218420.3 i/s - same-ish: difference falls within error
 Hash#fetch fallback: 53014731.0 i/s - same-ish: difference falls within error
          Hash#fetch: 52392431.9 i/s - same-ish: difference falls within error
            Hash#dig:  9914131.8 i/s - 5.48x  (± 0.00) slower

$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   332.687M i/100ms
  Hash#fetch + block   316.099M i/100ms
    Hash#fetch + arg   311.403M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      3.354B (± 3.5%) i/s -     16.967B in   5.065409s
  Hash#fetch + block      3.357B (± 4.2%) i/s -     16.753B in   5.000670s
    Hash#fetch + arg      3.356B (± 3.9%) i/s -     16.816B in   5.019302s

Comparison:
  Hash#fetch + block: 3356572065.8 i/s
    Hash#fetch + arg: 3355862113.1 i/s - same-ish: difference falls within error
  Hash#fetch + const: 3354084375.3 i/s - same-ish: difference falls within error

$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h     4.739k i/100ms
         sort + to_h     3.517k i/100ms
Calculating -------------------------------------
      sort_by + to_h    236.507k (±47.0%) i/s -    876.715k in   5.006900s
         sort + to_h     89.370k (± 6.7%) i/s -    446.659k in   5.022164s

Comparison:
      sort_by + to_h:   236507.2 i/s
         sort + to_h:    89369.8 i/s - 2.65x  (± 0.00) slower

$ ruby -v code/hash/keys-each-vs-each_key.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each   237.978k i/100ms
       Hash#each_key   264.825k i/100ms
Calculating -------------------------------------
      Hash#keys.each      2.329M (± 4.3%) i/s -     11.661M in   5.016453s
       Hash#each_key      2.625M (± 4.7%) i/s -     13.241M in   5.055554s

Comparison:
       Hash#each_key:  2625479.6 i/s
      Hash#keys.each:  2329368.4 i/s - 1.13x  (± 0.00) slower

$ ruby -v code/hash/keys-include-vs-key.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?    57.000  i/100ms
           Hash#key?    11.272M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      3.599k (±12.5%) i/s -     17.613k in   5.004005s
           Hash#key?    110.634M (± 4.2%) i/s -    552.326M in   5.002303s

Comparison:
           Hash#key?: 110633504.4 i/s
  Hash#keys.include?:     3599.2 i/s - 30738.36x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-[]=.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    11.942k i/100ms
            Hash#[]=    54.070k i/100ms
Calculating -------------------------------------
         Hash#merge!    519.165k (± 7.1%) i/s -      2.591M in   5.018318s
            Hash#[]=    535.860k (± 4.4%) i/s -      2.704M in   5.055598s

Comparison:
            Hash#[]=:   535859.7 i/s
         Hash#merge!:   519164.6 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                        24.877k i/100ms
      Hash#merge({})    16.221k i/100ms
 Hash#dup#merge!({})    26.230k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        266.424k (± 4.1%) i/s -      1.343M in   5.051376s
      Hash#merge({})    159.653k (± 7.4%) i/s -    794.829k in   5.021094s
 Hash#dup#merge!({})    259.157k (± 7.3%) i/s -      1.285M in   5.000774s

Comparison:
{}#merge!(Hash) do end:   266423.6 i/s
 Hash#dup#merge!({}):   259156.9 i/s - same-ish: difference falls within error
      Hash#merge({}):   159652.8 i/s - 1.67x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-double-splat-operator.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   329.071M i/100ms
          Hash#merge   337.584M i/100ms
Calculating -------------------------------------
        Hash#**other      3.360B (± 3.2%) i/s -     16.783B in   5.000888s
          Hash#merge      3.336B (± 4.6%) i/s -     16.879B in   5.071840s

Comparison:
        Hash#**other: 3359758966.8 i/s
          Hash#merge: 3335827196.2 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-vs-merge-bang.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge    98.000  i/100ms
         Hash#merge!    56.857k i/100ms
Calculating -------------------------------------
          Hash#merge      9.516k (±10.7%) i/s -     46.452k in   5.001056s
         Hash#merge!    542.928k (± 3.9%) i/s -      2.729M in   5.035265s

Comparison:
         Hash#merge!:   542927.6 i/s
          Hash#merge:     9516.3 i/s - 57.05x  (± 0.00) slower

$ ruby -v code/hash/slice-native-vs-before-native.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice        1.855M i/100ms
Array#each               1.519M i/100ms
Array#each_w/_object     1.549M i/100ms
Hash#select-include      2.207M i/100ms
Calculating -------------------------------------
Hash#native-slice        18.096M (± 3.8%) i/s -     90.898M in   5.030749s
Array#each               15.010M (± 3.7%) i/s -     75.957M in   5.067986s
Array#each_w/_object     14.689M (± 3.5%) i/s -     74.370M in   5.069578s
Hash#select-include      21.437M (± 4.9%) i/s -    108.154M in   5.058122s

Comparison:
Hash#select-include : 21437486.0 i/s
Hash#native-slice   : 18096323.2 i/s - 1.18x  (± 0.00) slower
Array#each          : 15010365.1 i/s - 1.43x  (± 0.00) slower
Array#each_w/_object: 14689492.6 i/s - 1.46x  (± 0.00) slower

$ ruby -v code/hash/values-include-vs-value.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?    77.000  i/100ms
         Hash#value?   144.000  i/100ms
Calculating -------------------------------------
Hash#values.include?      3.478k (±11.2%) i/s -     17.171k in   5.018333s
         Hash#value?      7.898k (± 7.1%) i/s -     39.312k in   5.005016s

Comparison:
         Hash#value?:     7897.8 i/s
Hash#values.include?:     3477.7 i/s - 2.27x  (± 0.00) slower

$ ruby -v code/method/call-vs-send-vs-method_missing.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   316.656M i/100ms
                send   336.711M i/100ms
      method_missing   336.246M i/100ms
Calculating -------------------------------------
                call      3.358B (± 3.7%) i/s -     16.783B in   5.006230s
                send      3.373B (± 3.2%) i/s -     17.172B in   5.097017s
      method_missing      3.361B (± 3.6%) i/s -     16.812B in   5.009400s

Comparison:
                send: 3372972179.3 i/s
      method_missing: 3361052106.1 i/s - same-ish: difference falls within error
                call: 3357640948.7 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/block-vs-to_proc.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    58.570k i/100ms
      Symbol#to_proc    64.181k i/100ms
Calculating -------------------------------------
               Block    627.104k (± 9.5%) i/s -      3.104M in   5.026331s
      Symbol#to_proc    618.920k (± 7.7%) i/s -      3.081M in   5.030425s

Comparison:
               Block:   627103.9 i/s
      Symbol#to_proc:   618919.5 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   303.183M i/100ms
       block + yield   336.961M i/100ms
        unused block   332.509M i/100ms
               yield   337.164M i/100ms
Calculating -------------------------------------
          block.call      3.351B (± 3.4%) i/s -     16.978B in   5.073138s
       block + yield      3.303B (± 6.0%) i/s -     16.511B in   5.020549s
        unused block      3.316B (± 4.7%) i/s -     16.625B in   5.025152s
               yield      3.328B (± 4.7%) i/s -     16.858B in   5.077280s

Comparison:
          block.call: 3351036982.4 i/s
               yield: 3328467459.1 i/s - same-ish: difference falls within error
        unused block: 3316477693.8 i/s - same-ish: difference falls within error
       block + yield: 3302569342.2 i/s - same-ish: difference falls within error

$ ruby -v code/range/cover-vs-include.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?     3.475M i/100ms
      range#include?     5.915k i/100ms
       range#member?     5.989k i/100ms
       plain compare     8.511M i/100ms
Calculating -------------------------------------
        range#cover?     49.512M (± 9.3%) i/s -    243.263M in   5.025212s
      range#include?     98.738k (± 4.9%) i/s -    496.860k in   5.045243s
       range#member?     99.670k (± 5.3%) i/s -    497.087k in   5.002484s
       plain compare     82.678M (± 6.4%) i/s -    417.055M in   5.067227s

Comparison:
       plain compare: 82677836.0 i/s
        range#cover?: 49511594.3 i/s - 1.67x  (± 0.00) slower
       range#member?:    99670.5 i/s - 829.51x  (± 0.00) slower
      range#include?:    98738.3 i/s - 837.34x  (± 0.00) slower

$ ruby -v code/string/===-vs-=~-vs-match.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     1.613M i/100ms
           String#=~     1.628M i/100ms
          Regexp#===     1.628M i/100ms
        String#match     1.455M i/100ms
Calculating -------------------------------------
       String#match?     16.410M (± 3.2%) i/s -     82.249M in   5.017789s
           String#=~     16.196M (± 4.0%) i/s -     81.387M in   5.034224s
          Regexp#===     15.932M (± 3.3%) i/s -     79.761M in   5.012461s
        String#match     15.682M (± 3.5%) i/s -     78.568M in   5.016608s

Comparison:
       String#match?: 16410016.5 i/s
           String#=~: 16195941.9 i/s - same-ish: difference falls within error
          Regexp#===: 15932135.9 i/s - same-ish: difference falls within error
        String#match: 15682023.1 i/s - same-ish: difference falls within error

$ ruby -v code/string/casecmp-vs-downcase-==.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.435M i/100ms
      String#casecmp     4.977M i/100ms
Calculating -------------------------------------
String#downcase + ==     25.711M (± 3.2%) i/s -    129.057M in   5.025174s
      String#casecmp     49.313M (± 3.4%) i/s -    248.871M in   5.053328s

Comparison:
      String#casecmp: 49312661.5 i/s
String#downcase + ==: 25710730.9 i/s - 1.92x  (± 0.00) slower

$ ruby -v code/string/concatenation.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   340.126M i/100ms
       String#concat   339.820M i/100ms
       String#append   349.230M i/100ms
         "foo" "bar"   349.072M i/100ms
  "#{'foo'}#{'bar'}"   349.158M i/100ms
Calculating -------------------------------------
            String#+      3.398B (± 4.7%) i/s -     17.006B in   5.017287s
       String#concat      3.409B (± 3.6%) i/s -     17.331B in   5.091802s
       String#append      3.418B (± 3.7%) i/s -     17.112B in   5.013682s
         "foo" "bar"      3.429B (± 3.9%) i/s -     17.454B in   5.099074s
  "#{'foo'}#{'bar'}"      3.406B (± 4.4%) i/s -     17.109B in   5.034275s

Comparison:
         "foo" "bar": 3429028536.4 i/s
       String#append: 3418184328.0 i/s - same-ish: difference falls within error
       String#concat: 3408686863.7 i/s - same-ish: difference falls within error
  "#{'foo'}#{'bar'}": 3405603889.8 i/s - same-ish: difference falls within error
            String#+: 3397943787.8 i/s - same-ish: difference falls within error

$ ruby -v code/string/dup-vs-unary-plus.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   324.831M i/100ms
          String#dup   346.858M i/100ms
Calculating -------------------------------------
           String#+@      3.410B (± 4.2%) i/s -     17.216B in   5.059099s
          String#dup      3.400B (± 4.4%) i/s -     17.343B in   5.111138s

Comparison:
           String#+@: 3409624065.7 i/s
          String#dup: 3400275302.6 i/s - same-ish: difference falls within error

$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   168.839k i/100ms
       String#match?   212.440k i/100ms
    String#end_with?   940.847k i/100ms
Calculating -------------------------------------
           String#=~      2.205M (± 5.2%) i/s -     11.143M in   5.069295s
       String#match?      2.204M (± 4.9%) i/s -     11.047M in   5.024248s
    String#end_with?     10.261M (± 4.8%) i/s -     51.747M in   5.054981s

Comparison:
    String#end_with?: 10261341.0 i/s
           String#=~:  2204686.2 i/s - 4.65x  (± 0.00) slower
       String#match?:  2204454.1 i/s - 4.65x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-sub.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub     7.914k i/100ms
          String#sub    86.211k i/100ms
String#dup["string"]=
                         6.413M i/100ms
Calculating -------------------------------------
         String#gsub    918.138k (± 7.8%) i/s -      4.558M in   4.998230s
          String#sub    900.427k (± 6.6%) i/s -      4.483M in   5.001743s
String#dup["string"]=
                         62.799M (± 5.0%) i/s -    314.222M in   5.017890s

Comparison:
String#dup["string"]=: 62799031.5 i/s
         String#gsub:   918138.2 i/s - 68.40x  (± 0.00) slower
          String#sub:   900427.1 i/s - 69.74x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-tr.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    14.918k i/100ms
           String#tr   257.197k i/100ms
Calculating -------------------------------------
         String#gsub      2.774M (±10.5%) i/s -     13.680M in   4.998055s
           String#tr      2.522M (± 5.8%) i/s -     12.603M in   5.014059s

Comparison:
         String#gsub:  2773582.3 i/s
           String#tr:  2522326.7 i/s - same-ish: difference falls within error

$ ruby -v code/string/mutable_vs_immutable_strings.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze   303.302M i/100ms
         With Freeze   319.418M i/100ms
Calculating -------------------------------------
      Without Freeze      3.428B (± 3.6%) i/s -     17.288B in   5.050729s
         With Freeze      3.398B (± 4.7%) i/s -     17.249B in   5.088673s

Comparison:
      Without Freeze: 3427661040.6 i/s
         With Freeze: 3397762155.5 i/s - same-ish: difference falls within error

$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/   658.000  i/100ms
      String#squeeze    59.889k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     56.371k (± 8.4%) i/s -    279.650k in   4.998523s
      String#squeeze    612.650k (± 5.7%) i/s -      3.054M in   5.003116s

Comparison:
      String#squeeze:   612649.8 i/s
 String#gsub/regex+/:    56370.6 i/s - 10.87x  (± 0.00) slower

$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   783.455k i/100ms
       String#match?   729.092k i/100ms
  String#start_with?     2.791M i/100ms
Calculating -------------------------------------
           String#=~      7.500M (± 5.7%) i/s -     37.606M in   5.032045s
       String#match?      7.951M (± 6.0%) i/s -     40.100M in   5.062754s
  String#start_with?     28.599M (± 6.4%) i/s -    145.133M in   5.096704s

Comparison:
  String#start_with?: 28598606.1 i/s
       String#match?:  7950970.2 i/s - 3.60x  (± 0.00) slower
           String#=~:  7499997.4 i/s - 3.81x  (± 0.00) slower

$ ruby -v code/string/start_with-vs-substring-==.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?    31.668k i/100ms
    String#[0, n] ==   409.680k i/100ms
   String#[RANGE] ==   433.859k i/100ms
   String#[0...n] ==   296.755k i/100ms
Calculating -------------------------------------
  String#start_with?      4.720M (± 8.7%) i/s -     23.371M in   4.997393s
    String#[0, n] ==      3.884M (± 8.7%) i/s -     19.255M in   5.010651s
   String#[RANGE] ==      4.200M (± 5.4%) i/s -     21.259M in   5.077345s
   String#[0...n] ==      3.283M (± 5.8%) i/s -     16.618M in   5.079931s

Comparison:
  String#start_with?:  4720033.7 i/s
   String#[RANGE] ==:  4200396.7 i/s - same-ish: difference falls within error
    String#[0, n] ==:  3884000.2 i/s - 1.22x  (± 0.00) slower
   String#[0...n] ==:  3282917.1 i/s - 1.44x  (± 0.00) slower

$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=     6.741M i/100ms
 String#sub!'string'    85.484k i/100ms
String#gsub!'string'    96.603k i/100ms
  String#[/regexp/]=   624.007k i/100ms
 String#sub!/regexp/   619.515k i/100ms
String#gsub!/regexp/   116.334k i/100ms
Calculating -------------------------------------
  String#['string']=     65.721M (± 4.8%) i/s -    330.317M in   5.038421s
 String#sub!'string'    934.150k (± 4.8%) i/s -      4.702M in   5.045285s
String#gsub!'string'    939.868k (± 4.4%) i/s -      4.734M in   5.046988s
  String#[/regexp/]=      5.966M (± 5.9%) i/s -     29.952M in   5.039507s
 String#sub!/regexp/      6.345M (± 5.5%) i/s -     32.215M in   5.093410s
String#gsub!/regexp/      2.670M (± 6.8%) i/s -     13.378M in   5.034422s

Comparison:
  String#['string']=: 65721017.6 i/s
 String#sub!/regexp/:  6344997.7 i/s - 10.36x  (± 0.00) slower
  String#[/regexp/]=:  5965867.2 i/s - 11.02x  (± 0.00) slower
String#gsub!/regexp/:  2670308.4 i/s - 24.61x  (± 0.00) slower
String#gsub!'string':   939867.7 i/s - 69.93x  (± 0.00) slower
 String#sub!'string':   934149.9 i/s - 70.35x  (± 0.00) slower

$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub   522.289k i/100ms
        String#chomp     2.345M i/100ms
String#delete_suffix     2.353M i/100ms
Calculating -------------------------------------
          String#sub      5.748M (± 5.1%) i/s -     28.726M in   5.011783s
        String#chomp     24.305M (± 5.6%) i/s -    121.966M in   5.035417s
String#delete_suffix     24.228M (± 5.9%) i/s -    122.380M in   5.070282s

Comparison:
        String#chomp: 24304613.3 i/s
String#delete_suffix: 24227559.8 i/s - same-ish: difference falls within error
          String#sub:  5747851.7 i/s - 4.23x  (± 0.00) slower

$ ruby -v code/string/sub-vs-delete_prefix.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     4.096M i/100ms
          String#sub   686.848k i/100ms
Calculating -------------------------------------
String#delete_prefix     39.872M (± 5.2%) i/s -    200.725M in   5.049042s
          String#sub      6.876M (± 5.9%) i/s -     34.342M in   5.012763s

Comparison:
String#delete_prefix: 39872221.3 i/s
          String#sub:  6876211.9 i/s - 5.80x  (± 0.00) slower

$ ruby -v code/string/unpack1-vs-unpack[0].rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     1.972M i/100ms
    String#unpack[0]     2.093M i/100ms
Calculating -------------------------------------
      String#unpack1     22.220M (± 4.3%) i/s -    112.409M in   5.069321s
    String#unpack[0]     22.209M (± 6.0%) i/s -    110.955M in   5.015710s

Comparison:
      String#unpack1: 22219920.3 i/s
    String#unpack[0]: 22209283.8 i/s - same-ish: difference falls within error

$ ruby -v code/time/iso8601-vs-parse.rb
truffleruby 21.0.0-dev-6d65f3de, like ruby 2.7.2, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601     3.520k i/100ms
          Time.parse   804.000  i/100ms
Calculating -------------------------------------
        Time.iso8601    320.585k (± 9.4%) i/s -      1.588M in   5.002310s
          Time.parse     43.620k (± 7.0%) i/s -    217.080k in   5.004152s

Comparison:
        Time.iso8601:   320584.9 i/s
          Time.parse:    43619.9 i/s - 7.35x  (± 0.00) slower

```



## License

![CC-BY-SA](CC-BY-SA.png)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Code License

### CC0 1.0 Universal

To the extent possible under law, @JuanitoFatas has waived all copyright and related or neighboring rights to "fast-ruby".

This work belongs to the community.
