## Fast Truffle Ruby 


The idia of this project is to run all collected examples from the [Fast Ruby] (https://github.com/JuanitoFatas/fast-ruby) and run it against the latest truffle ruby version to see if the same results hold for the Truffle ruby. 

As you will see in the resalst below some results a quite different

## Results
```
truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       214.938M i/100ms
Function with splat arguments
                       695.000  i/100ms
Calculating -------------------------------------
Function with single Array argument
                          2.044B (± 8.0%) i/s -     10.317B in   5.081814s
Function with splat arguments
                          8.641k (±26.8%) i/s -     39.615k in   5.045479s

Comparison:
Function with single Array argument: 2044021263.4 i/s
Function with splat arguments:     8641.2 i/s - 236543.63x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   185.085M i/100ms
Sequential Assignment
                       198.450M i/100ms
Calculating -------------------------------------
 Parallel Assignment      1.965B (± 7.9%) i/s -      9.809B in   5.023674s
Sequential Assignment
                          1.958B (± 7.7%) i/s -      9.923B in   5.097641s

Comparison:
 Parallel Assignment: 1964779048.5 i/s
Sequential Assignment: 1958045109.4 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   202.067M i/100ms
       attr_accessor   221.292M i/100ms
Calculating -------------------------------------
   getter_and_setter      2.136B (± 5.9%) i/s -     10.710B in   5.033260s
       attr_accessor      2.042B (± 6.8%) i/s -     10.179B in   5.009439s

Comparison:
   getter_and_setter: 2135886888.8 i/s
       attr_accessor: 2041724987.7 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     7.710k i/100ms
         respond_to?   217.069M i/100ms
Calculating -------------------------------------
      begin...rescue     72.919k (±15.7%) i/s -    354.660k in   5.029199s
         respond_to?      2.121B (± 5.9%) i/s -     10.636B in   5.033198s

Comparison:
         respond_to?: 2121113183.4 i/s
      begin...rescue:    72919.0 i/s - 29088.62x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   215.335M i/100ms
             &method   220.353M i/100ms
Calculating -------------------------------------
              normal      2.117B (± 6.2%) i/s -     10.551B in   5.005583s
             &method      2.134B (± 5.8%) i/s -     10.797B in   5.077513s

Comparison:
             &method: 2134159886.5 i/s
              normal: 2116740516.9 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                        15.000  i/100ms
       define_method    35.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.655k (±34.6%) i/s -      4.920k in   5.058299s
       define_method      2.786k (±34.2%) i/s -      8.120k in   5.016982s

Comparison:
       define_method:     2785.6 i/s
module_eval with string:     1655.1 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    56.703k i/100ms
       Kernel#format    74.590k i/100ms
            String#%    70.956k i/100ms
Calculating -------------------------------------
         Float#round    548.666k (±13.2%) i/s -      2.722M in   5.073582s
       Kernel#format    775.648k (± 7.7%) i/s -      3.879M in   5.033009s
            String#%    767.355k (± 9.6%) i/s -      3.832M in   5.054271s

Comparison:
       Kernel#format:   775648.3 i/s
            String#%:   767354.8 i/s - same-ish: difference falls within error
         Float#round:   548665.6 i/s - 1.41x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   301.435M i/100ms
          OpenStruct   221.810M i/100ms
Calculating -------------------------------------
                Hash      3.342B (± 6.7%) i/s -     16.880B in   5.074903s
          OpenStruct      2.139B (± 5.6%) i/s -     10.869B in   5.098687s

Comparison:
                Hash: 3342014045.8 i/s
          OpenStruct: 2139049816.5 i/s - 1.56x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   188.302M i/100ms
          OpenStruct   220.266M i/100ms
Calculating -------------------------------------
                Hash      2.127B (± 6.4%) i/s -     10.733B in   5.067752s
          OpenStruct      2.139B (± 6.0%) i/s -     10.793B in   5.066332s

Comparison:
          OpenStruct: 2138672810.3 i/s
                Hash: 2127435048.3 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal     1.021M i/100ms
  ancestors.include?   133.238k i/100ms
Calculating -------------------------------------
  less than or equal      9.604M (±13.7%) i/s -     46.946M in   5.006771s
  ancestors.include?      1.220M (±16.2%) i/s -      5.996M in   5.092172s

Comparison:
  less than or equal:  9603977.2 i/s
  ancestors.include?:  1220137.4 i/s - 7.87x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     1.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     32.484  (± 6.2%) i/s -    162.000  in   5.011357s
         Kernel loop      8.012  (±12.5%) i/s -     40.000  in   5.014926s

Comparison:
          While Loop:       32.5 i/s
         Kernel loop:        8.0 i/s - 4.05x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Ruby exception: E2MM#Raise
                       364.000  i/100ms
Ruby exception: Kernel#raise
                       199.245M i/100ms
Calculating -------------------------------------
Ruby exception: E2MM#Raise
                          8.244k (±20.7%) i/s -     38.584k in   5.029210s
Ruby exception: Kernel#raise
                          2.067B (± 7.0%) i/s -     10.361B in   5.039058s
Warming up --------------------------------------
Custom exception: E2MM#Raise
                       284.000  i/100ms
Custom exception: Kernel#raise
                       161.732M i/100ms
Calculating -------------------------------------
Custom exception: E2MM#Raise
                          8.237k (±21.1%) i/s -     38.056k in   5.010928s
Custom exception: Kernel#raise
                          2.034B (± 6.9%) i/s -     10.189B in   5.033517s

Comparison:
Ruby exception: Kernel#raise: 2066603499.1 i/s
Ruby exception: E2MM#Raise:     8243.8 i/s - 250684.49x  (± 0.00) slower


Comparison:
Custom exception: Kernel#raise: 2034295009.3 i/s
Custom exception: E2MM#Raise:     8236.8 i/s - 246975.85x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   209.826M i/100ms
         Array#first   215.288M i/100ms
Calculating -------------------------------------
           Array#[0]      2.021B (± 6.2%) i/s -     10.072B in   5.003717s
         Array#first      1.952B (± 7.9%) i/s -      9.903B in   5.105119s

Comparison:
           Array#[0]: 2020898855.5 i/s
         Array#first: 1952100601.3 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   330.470M i/100ms
          Array#last   337.523M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.169B (± 5.7%) i/s -     15.863B in   5.021897s
          Array#last      3.152B (± 7.0%) i/s -     15.864B in   5.056676s

Comparison:
          Array#[-1]: 3168936413.7 i/s
          Array#last: 3152468421.4 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   263.241k i/100ms
Calculating -------------------------------------
                find      0.063  (± 0.0%) i/s -      1.000  in  15.899282s
             bsearch      3.095M (±21.6%) i/s -     14.741M in   5.043974s

Comparison:
             bsearch:  3095074.1 i/s
                find:        0.1 i/s - 49209454.76x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.160  (± 0.0%) i/s -      1.000  in   6.267281s
        Array#insert      0.296  (± 0.0%) i/s -      2.000  in   6.769449s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.85x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   346.304M i/100ms
          Array#size   354.880M i/100ms
         Array#count   102.493M i/100ms
Calculating -------------------------------------
        Array#length      3.405B (± 6.1%) i/s -     16.969B in   5.003656s
          Array#size      3.329B (± 6.3%) i/s -     16.679B in   5.030619s
         Array#count    988.179M (± 6.5%) i/s -      4.920B in   5.000866s

Comparison:
        Array#length: 3405330635.8 i/s
          Array#size: 3329379323.9 i/s - same-ish: difference falls within error
         Array#count: 988179228.7 i/s - 3.45x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first     4.479k i/100ms
        Array#sample     1.245M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    115.158k (± 9.7%) i/s -    568.833k in   5.033736s
        Array#sample     11.323M (± 7.9%) i/s -     57.255M in   5.088318s

Comparison:
        Array#sample: 11323376.3 i/s
 Array#shuffle.first:   115157.8 i/s - 98.33x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601   108.000  i/100ms
          Date.parse   340.000  i/100ms
Calculating -------------------------------------
        Date.iso8601     25.473k (±26.7%) i/s -     97.632k in   4.994582s
          Date.parse     26.489k (±20.0%) i/s -    118.660k in   4.999892s

Comparison:
          Date.parse:    26488.6 i/s
        Date.iso8601:    25472.9 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   206.100k i/100ms
           Array#map   822.083k i/100ms
Calculating -------------------------------------
   Array#each + push      2.186M (±19.1%) i/s -     10.717M in   5.147168s
           Array#map      7.365M (±18.8%) i/s -     35.350M in   5.030113s

Comparison:
           Array#map:  7365434.9 i/s
   Array#each + push:  2186031.4 i/s - 3.37x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop   493.156k i/100ms
               #each   660.949k i/100ms
Calculating -------------------------------------
            For loop      5.448M (± 6.6%) i/s -     27.124M in   5.001431s
               #each      6.355M (± 5.6%) i/s -     31.726M in   5.009719s

Comparison:
               #each:  6354665.9 i/s
            For loop:  5448384.9 i/s - 1.17x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   501.597k i/100ms
     each_with_index   571.025k i/100ms
Calculating -------------------------------------
          While Loop      4.829M (± 5.5%) i/s -     24.077M in   5.002685s
     each_with_index      5.575M (± 5.2%) i/s -     27.980M in   5.033568s

Comparison:
     each_with_index:  5575248.4 i/s
          While Loop:  4828829.9 i/s - 1.15x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   213.388k i/100ms
      inject to_proc    20.454k i/100ms
        inject block   183.057k i/100ms
Calculating -------------------------------------
       inject symbol      2.061M (± 6.1%) i/s -     10.456M in   5.094671s
      inject to_proc    202.481k (± 5.9%) i/s -      1.023M in   5.070471s
        inject block      2.063M (± 5.9%) i/s -     10.434M in   5.076712s

Comparison:
        inject block:  2063119.4 i/s
       inject symbol:  2060730.4 i/s - same-ish: difference falls within error
      inject to_proc:   202481.2 i/s - 10.19x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    13.993k i/100ms
   Array#map.flatten    10.276k i/100ms
      Array#flat_map    29.237k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    217.771k (±23.7%) i/s -      1.007M in   5.005387s
   Array#map.flatten    101.620k (±21.6%) i/s -    482.972k in   5.071910s
      Array#flat_map    275.869k (±15.2%) i/s -      1.345M in   5.022220s

Comparison:
      Array#flat_map:   275869.0 i/s
Array#map.flatten(1):   217771.1 i/s - same-ish: difference falls within error
   Array#map.flatten:   101619.8 i/s - 2.71x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   214.406k i/100ms
  Array#reverse_each   504.510k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.074M (±12.3%) i/s -     10.291M in   5.068050s
  Array#reverse_each      4.820M (± 6.7%) i/s -     24.216M in   5.048040s

Comparison:
  Array#reverse_each:  4819904.6 i/s
  Array#reverse.each:  2074378.3 i/s - 2.32x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       403.449k i/100ms
   Enumerable#detect     3.507M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          3.836M (±16.7%) i/s -     74.235M in  20.060651s
   Enumerable#detect     40.112M (± 5.7%) i/s -    803.170M in  20.095808s

Comparison:
   Enumerable#detect: 40112304.3 i/s
Enumerable#select.first:  3836052.5 i/s - 10.46x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       219.237k i/100ms
Enumerable#select.last
                       291.357k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.226M (±13.9%) i/s -     10.962M in   5.058372s
Enumerable#select.last
                          3.040M (±14.7%) i/s -     14.859M in   5.036109s

Comparison:
Enumerable#select.last:  3040009.0 i/s
Enumerable#reverse.detect:  2225898.3 i/s - 1.37x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         1.362k i/100ms
  Enumerable#sort_by   102.000  i/100ms
     Enumerable#sort     2.087k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         49.553k (±27.8%) i/s -    160.716k in   5.002091s
  Enumerable#sort_by     31.313k (±17.6%) i/s -    127.194k in   4.995740s
     Enumerable#sort     35.368k (±20.1%) i/s -    166.960k in   5.008169s

Comparison:
Enumerable#sort_by (Symbol#to_proc):    49552.6 i/s
     Enumerable#sort:    35368.5 i/s - same-ish: difference falls within error
  Enumerable#sort_by:    31312.8 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   300.326k i/100ms
Enumerable#sort_by...first
                         9.701k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      3.287M (± 6.8%) i/s -     16.518M in   5.050788s
Enumerable#sort_by...first
                        102.714k (±15.0%) i/s -    504.452k in   5.067481s

Comparison:
   Enumerable#min_by:  3286631.8 i/s
Enumerable#sort_by...first:   102714.2 i/s - 32.00x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   273.241k i/100ms
            Hash#dup   251.758k i/100ms
Calculating -------------------------------------
              Hash[]      2.736M (±20.7%) i/s -     13.389M in   5.155655s
            Hash#dup      2.861M (±23.2%) i/s -     13.343M in   5.028232s

Comparison:
            Hash#dup:  2860686.6 i/s
              Hash[]:  2735798.9 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   338.945M i/100ms
  Hash#fetch, symbol   101.827M i/100ms
     Hash#[], string     5.556M i/100ms
  Hash#fetch, string     4.846M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      3.012B (± 6.1%) i/s -     15.253B in   5.083048s
  Hash#fetch, symbol    870.765M (±13.9%) i/s -      4.277B in   5.104433s
     Hash#[], string     50.415M (± 6.3%) i/s -    255.569M in   5.090168s
  Hash#fetch, string     52.972M (± 6.6%) i/s -    266.522M in   5.054625s

Comparison:
     Hash#[], symbol: 3011559918.9 i/s
  Hash#fetch, symbol: 870764822.4 i/s - 3.46x  (± 0.00) slower
  Hash#fetch, string: 52972310.5 i/s - 56.85x  (± 0.00) slower
     Hash#[], string: 50415453.1 i/s - 59.73x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig   732.641k i/100ms
             Hash#[]     4.935M i/100ms
          Hash#[] ||     4.264M i/100ms
          Hash#[] &&   192.872k i/100ms
          Hash#fetch     3.008M i/100ms
 Hash#fetch fallback     2.950M i/100ms
Calculating -------------------------------------
            Hash#dig      7.684M (±17.8%) i/s -     37.365M in   5.059809s
             Hash#[]     47.513M (± 6.2%) i/s -    236.861M in   5.006080s
          Hash#[] ||     40.991M (± 6.0%) i/s -    204.653M in   5.012093s
          Hash#[] &&     15.512M (± 6.6%) i/s -     77.149M in   4.998266s
          Hash#fetch     28.989M (± 5.6%) i/s -    147.368M in   5.100545s
 Hash#fetch fallback     28.779M (± 5.7%) i/s -    144.549M in   5.039588s

Comparison:
             Hash#[]: 47512759.9 i/s
          Hash#[] ||: 40990506.8 i/s - 1.16x  (± 0.00) slower
          Hash#fetch: 28988700.4 i/s - 1.64x  (± 0.00) slower
 Hash#fetch fallback: 28778942.5 i/s - 1.65x  (± 0.00) slower
          Hash#[] &&: 15512422.2 i/s - 3.06x  (± 0.00) slower
            Hash#dig:  7684323.2 i/s - 6.18x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   211.469M i/100ms
  Hash#fetch + block   218.393M i/100ms
    Hash#fetch + arg   219.404M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      2.107B (± 6.2%) i/s -     10.573B in   5.039018s
  Hash#fetch + block      2.127B (± 6.4%) i/s -     10.701B in   5.053230s
    Hash#fetch + arg      2.119B (± 5.6%) i/s -     10.751B in   5.090494s

Comparison:
  Hash#fetch + block: 2127233893.6 i/s
    Hash#fetch + arg: 2119123319.2 i/s - same-ish: difference falls within error
  Hash#fetch + const: 2107016282.4 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h     3.984k i/100ms
         sort + to_h   148.000  i/100ms
Calculating -------------------------------------
      sort_by + to_h    356.139k (±37.9%) i/s -    717.120k in   5.005609s
         sort + to_h    194.182k (±16.7%) i/s -    716.764k in   4.991755s

Comparison:
      sort_by + to_h:   356138.5 i/s
         sort + to_h:   194182.2 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each   847.398k i/100ms
       Hash#each_key     1.752M i/100ms
Calculating -------------------------------------
      Hash#keys.each     11.394M (±15.8%) i/s -     55.081M in   5.005517s
       Hash#each_key     16.999M (± 6.0%) i/s -     85.834M in   5.069232s

Comparison:
       Hash#each_key: 16999002.5 i/s
      Hash#keys.each: 11394104.1 i/s - 1.49x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?    51.000  i/100ms
           Hash#key?     3.507M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      4.283k (±18.6%) i/s -     18.972k in   4.997820s
           Hash#key?     38.014M (± 6.0%) i/s -    189.366M in   5.001291s

Comparison:
           Hash#key?: 38014430.1 i/s
  Hash#keys.include?:     4283.0 i/s - 8875.68x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    22.287k i/100ms
            Hash#[]=    33.365k i/100ms
Calculating -------------------------------------
         Hash#merge!    378.633k (±25.4%) i/s -      1.738M in   5.038139s
            Hash#[]=    363.192k (±19.4%) i/s -      1.735M in   5.034080s

Comparison:
         Hash#merge!:   378633.2 i/s
            Hash#[]=:   363192.3 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                        12.481k i/100ms
      Hash#merge({})     9.078k i/100ms
 Hash#dup#merge!({})    16.233k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        145.797k (±29.5%) i/s -    649.012k in   5.010981s
      Hash#merge({})     86.499k (±23.9%) i/s -    408.510k in   5.055230s
 Hash#dup#merge!({})    143.716k (±21.8%) i/s -    698.019k in   5.145199s

Comparison:
{}#merge!(Hash) do end:   145796.9 i/s
 Hash#dup#merge!({}):   143716.4 i/s - same-ish: difference falls within error
      Hash#merge({}):    86499.1 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   367.694k i/100ms
          Hash#merge   199.081M i/100ms
Calculating -------------------------------------
        Hash#**other      6.834M (±24.8%) i/s -     31.254M in   5.040594s
          Hash#merge      2.131B (± 6.0%) i/s -     10.750B in   5.064823s

Comparison:
          Hash#merge: 2130841018.2 i/s
        Hash#**other:  6833902.6 i/s - 311.80x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge   123.000  i/100ms
         Hash#merge!    23.099k i/100ms
Calculating -------------------------------------
          Hash#merge      5.840k (±40.9%) i/s -     21.894k in   5.061286s
         Hash#merge!    330.543k (±25.6%) i/s -      1.525M in   5.027542s

Comparison:
         Hash#merge!:   330542.8 i/s
          Hash#merge:     5839.6 i/s - 56.60x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice      938.724k i/100ms
Array#each               1.003M i/100ms
Array#each_w/_object     1.324M i/100ms
Hash#select-include      1.508M i/100ms
Calculating -------------------------------------
Hash#native-slice        15.071M (±22.4%) i/s -     70.404M in   5.011189s
Array#each               12.635M (±19.0%) i/s -     60.196M in   5.013189s
Array#each_w/_object     11.680M (±16.9%) i/s -     56.921M in   5.063728s
Hash#select-include      13.593M (±17.3%) i/s -     66.373M in   5.075949s

Comparison:
Hash#native-slice   : 15070789.5 i/s
Hash#select-include : 13593473.9 i/s - same-ish: difference falls within error
Array#each          : 12634838.4 i/s - same-ish: difference falls within error
Array#each_w/_object: 11679554.9 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?    47.000  i/100ms
         Hash#value?    89.000  i/100ms
Calculating -------------------------------------
Hash#values.include?      3.691k (±22.4%) i/s -     14.993k in   5.002726s
         Hash#value?      8.516k (± 8.2%) i/s -     42.275k in   5.002428s

Comparison:
         Hash#value?:     8515.6 i/s
Hash#values.include?:     3690.7 i/s - 2.31x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   221.227M i/100ms
                send   186.698M i/100ms
      method_missing   199.176M i/100ms
Calculating -------------------------------------
                call      2.107B (± 5.8%) i/s -     10.619B in   5.057706s
                send      2.126B (± 5.9%) i/s -     10.642B in   5.023963s
      method_missing      2.134B (± 5.9%) i/s -     10.756B in   5.058595s

Comparison:
      method_missing: 2134367774.5 i/s
                send: 2126284730.6 i/s - same-ish: difference falls within error
                call: 2106937723.2 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    22.073k i/100ms
      Symbol#to_proc    23.543k i/100ms
Calculating -------------------------------------
               Block    312.496k (±28.2%) i/s -      1.413M in   5.029539s
      Symbol#to_proc    279.958k (±25.6%) i/s -      1.271M in   4.952397s

Comparison:
               Block:   312495.8 i/s
      Symbol#to_proc:   279958.4 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   220.103M i/100ms
       block + yield   219.449M i/100ms
        unused block   219.409M i/100ms
               yield   187.453M i/100ms
Calculating -------------------------------------
          block.call      2.081B (± 5.3%) i/s -     10.565B in   5.091756s
       block + yield      2.075B (± 5.2%) i/s -     10.534B in   5.091362s
        unused block      2.121B (± 6.3%) i/s -     10.751B in   5.090744s
               yield      2.131B (± 6.1%) i/s -     10.685B in   5.033912s

Comparison:
               yield: 2131182708.1 i/s
        unused block: 2121068014.1 i/s - same-ish: difference falls within error
          block.call: 2081247825.8 i/s - same-ish: difference falls within error
       block + yield: 2074809678.4 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?    54.655M i/100ms
      range#include?     3.262k i/100ms
       range#member?     7.336k i/100ms
       plain compare   351.881M i/100ms
Calculating -------------------------------------
        range#cover?      3.418B (±10.2%) i/s -     15.959B in   5.001384s
      range#include?    171.326k (±21.6%) i/s -    769.832k in   5.005073s
       range#member?    157.510k (±21.7%) i/s -    733.600k in   5.024606s
       plain compare      3.154B (± 9.6%) i/s -     15.835B in   5.071284s

Comparison:
        range#cover?: 3418451761.9 i/s
       plain compare: 3154177088.5 i/s - same-ish: difference falls within error
      range#include?:   171325.7 i/s - 19952.94x  (± 0.00) slower
       range#member?:   157509.8 i/s - 21703.10x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     1.008M i/100ms
           String#=~   221.882k i/100ms
          Regexp#===   202.817k i/100ms
        String#match    78.418k i/100ms
Calculating -------------------------------------
       String#match?      9.783M (±16.9%) i/s -     47.360M in   5.026451s
           String#=~      2.324M (±16.9%) i/s -     11.316M in   5.079782s
          Regexp#===      2.369M (±15.1%) i/s -     11.561M in   5.027069s
        String#match    930.332k (±13.2%) i/s -      4.627M in   5.087410s

Comparison:
       String#match?:  9783477.6 i/s
          Regexp#===:  2369077.4 i/s - 4.13x  (± 0.00) slower
           String#=~:  2324051.3 i/s - 4.21x  (± 0.00) slower
        String#match:   930331.7 i/s - 10.52x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.324M i/100ms
      String#casecmp     3.296M i/100ms
Calculating -------------------------------------
String#downcase + ==     24.022M (± 8.8%) i/s -    120.848M in   5.071443s
      String#casecmp     34.874M (± 5.9%) i/s -    174.663M in   5.027682s

Comparison:
      String#casecmp: 34874267.4 i/s
String#downcase + ==: 24021843.7 i/s - 1.45x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   212.604M i/100ms
       String#concat   209.003M i/100ms
       String#append   186.259M i/100ms
         "foo" "bar"   215.812M i/100ms
  "#{'foo'}#{'bar'}"   216.078M i/100ms
Calculating -------------------------------------
            String#+      2.066B (± 5.8%) i/s -     10.418B in   5.060022s
       String#concat      2.088B (± 5.4%) i/s -     10.450B in   5.020243s
       String#append      2.095B (± 5.2%) i/s -     10.617B in   5.082514s
         "foo" "bar"      2.104B (± 5.4%) i/s -     10.575B in   5.042430s
  "#{'foo'}#{'bar'}"      2.063B (± 5.9%) i/s -     10.372B in   5.045091s

Comparison:
         "foo" "bar": 2103829714.2 i/s
       String#append: 2095011812.5 i/s - same-ish: difference falls within error
       String#concat: 2088279186.8 i/s - same-ish: difference falls within error
            String#+: 2066263004.6 i/s - same-ish: difference falls within error
  "#{'foo'}#{'bar'}": 2063457461.5 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   347.370M i/100ms
          String#dup   300.693M i/100ms
Calculating -------------------------------------
           String#+@      3.218B (± 6.4%) i/s -     16.326B in   5.095079s
          String#dup      3.334B (± 6.1%) i/s -     16.839B in   5.069779s

Comparison:
          String#dup: 3334459202.6 i/s
           String#+@: 3218147880.3 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   117.807k i/100ms
       String#match?   211.171k i/100ms
    String#end_with?   449.793k i/100ms
Calculating -------------------------------------
           String#=~      1.156M (±13.0%) i/s -      5.655M in   5.006070s
       String#match?      2.064M (±14.6%) i/s -     10.136M in   5.065171s
    String#end_with?      5.482M (±20.7%) i/s -     26.088M in   5.069838s

Comparison:
    String#end_with?:  5482312.0 i/s
       String#match?:  2063832.0 i/s - 2.66x  (± 0.00) slower
           String#=~:  1156130.4 i/s - 4.74x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub     2.993k i/100ms
          String#sub     8.812k i/100ms
String#dup["string"]=
                       740.997k i/100ms
Calculating -------------------------------------
         String#gsub    781.840k (±12.9%) i/s -      3.663M in   4.996384s
          String#sub    373.189k (±21.0%) i/s -      1.692M in   5.014586s
String#dup["string"]=
                          8.806M (±18.5%) i/s -     42.237M in   5.038475s

Comparison:
String#dup["string"]=:  8805754.6 i/s
         String#gsub:   781839.5 i/s - 11.26x  (± 0.00) slower
          String#sub:   373188.9 i/s - 23.60x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub     4.127k i/100ms
           String#tr   187.145k i/100ms
Calculating -------------------------------------
         String#gsub      1.289M (±19.3%) i/s -      5.122M in   4.995205s
           String#tr      1.555M (±18.8%) i/s -      7.673M in   5.174490s

Comparison:
           String#tr:  1555315.4 i/s
         String#gsub:  1288636.0 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze    46.854k i/100ms
         With Freeze   179.937M i/100ms
Calculating -------------------------------------
      Without Freeze      2.908B (±27.8%) i/s -     12.630B in   4.900071s
         With Freeze      2.086B (± 5.8%) i/s -     10.436B in   5.021621s

Comparison:
      Without Freeze: 2907734562.3 i/s
         With Freeze: 2085773217.0 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/   938.000  i/100ms
      String#squeeze    56.922k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     30.041k (±27.2%) i/s -    131.320k in   4.999617s
      String#squeeze    589.448k (±15.1%) i/s -      2.903M in   5.095314s

Comparison:
      String#squeeze:   589447.6 i/s
 String#gsub/regex+/:    30041.1 i/s - 19.62x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   170.760k i/100ms
       String#match?   587.653k i/100ms
  String#start_with?     1.888M i/100ms
Calculating -------------------------------------
           String#=~      1.879M (±16.6%) i/s -      9.050M in   5.004820s
       String#match?      5.380M (±18.2%) i/s -     25.857M in   5.010524s
  String#start_with?     20.164M (±18.8%) i/s -     98.151M in   5.104619s

Comparison:
  String#start_with?: 20164428.5 i/s
       String#match?:  5379640.5 i/s - 3.75x  (± 0.00) slower
           String#=~:  1878620.9 i/s - 10.73x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?    20.331k i/100ms
    String#[0, n] ==   198.874k i/100ms
   String#[RANGE] ==    17.905k i/100ms
   String#[0...n] ==   137.029k i/100ms
Calculating -------------------------------------
  String#start_with?      3.355M (±21.7%) i/s -     13.703M in   4.994842s
    String#[0, n] ==      1.835M (±20.3%) i/s -      8.949M in   5.131973s
   String#[RANGE] ==      2.125M (±29.0%) i/s -      7.914M in   4.997178s
   String#[0...n] ==      1.305M (±22.5%) i/s -      6.166M in   5.036548s

Comparison:
  String#start_with?:  3354697.3 i/s
   String#[RANGE] ==:  2124982.4 i/s - same-ish: difference falls within error
    String#[0, n] ==:  1835314.7 i/s - 1.83x  (± 0.00) slower
   String#[0...n] ==:  1304570.3 i/s - 2.57x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=     5.254M i/100ms
 String#sub!'string'    52.428k i/100ms
String#gsub!'string'    52.526k i/100ms
  String#[/regexp/]=    66.747k i/100ms
 String#sub!/regexp/    54.611k i/100ms
String#gsub!/regexp/    29.907k i/100ms
Calculating -------------------------------------
  String#['string']=     49.615M (±10.4%) i/s -    246.927M in   5.068672s
 String#sub!'string'    494.507k (±15.8%) i/s -      2.412M in   5.043626s
String#gsub!'string'    662.437k (±22.2%) i/s -      2.994M in   5.049737s
  String#[/regexp/]=      1.651M (±20.9%) i/s -      7.676M in   5.016208s
 String#sub!/regexp/      1.647M (±20.4%) i/s -      7.646M in   5.024434s
String#gsub!/regexp/      1.090M (±22.3%) i/s -      4.905M in   4.998174s

Comparison:
  String#['string']=: 49615319.7 i/s
  String#[/regexp/]=:  1651465.6 i/s - 30.04x  (± 0.00) slower
 String#sub!/regexp/:  1647137.8 i/s - 30.12x  (± 0.00) slower
String#gsub!/regexp/:  1090070.3 i/s - 45.52x  (± 0.00) slower
String#gsub!'string':   662437.2 i/s - 74.90x  (± 0.00) slower
 String#sub!'string':   494506.9 i/s - 100.33x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub    53.601k i/100ms
        String#chomp     1.262M i/100ms
String#delete_suffix     1.088M i/100ms
Calculating -------------------------------------
          String#sub    812.627k (±16.2%) i/s -      3.913M in   5.021561s
        String#chomp     13.895M (±18.8%) i/s -     66.867M in   5.067101s
String#delete_suffix     13.678M (±19.9%) i/s -     65.257M in   5.046821s

Comparison:
        String#chomp: 13895459.4 i/s
String#delete_suffix: 13677650.9 i/s - same-ish: difference falls within error
          String#sub:   812626.6 i/s - 17.10x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     1.066M i/100ms
          String#sub    84.993k i/100ms
Calculating -------------------------------------
String#delete_prefix     19.257M (±20.8%) i/s -     90.572M in   5.033367s
          String#sub    812.231k (±14.2%) i/s -      3.995M in   5.046680s

Comparison:
String#delete_prefix: 19257311.1 i/s
          String#sub:   812231.2 i/s - 23.71x  (± 0.00) slower

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     1.744M i/100ms
    String#unpack[0]     1.769M i/100ms
Calculating -------------------------------------
      String#unpack1     16.038M (±16.2%) i/s -     78.470M in   5.067201s
    String#unpack[0]     16.649M (±17.6%) i/s -     81.365M in   5.089618s

Comparison:
    String#unpack[0]: 16648535.4 i/s
      String#unpack1: 16038150.6 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-c60f3a13, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601   872.000  i/100ms
          Time.parse   411.000  i/100ms
Calculating -------------------------------------
        Time.iso8601    118.352k (±21.9%) i/s -    476.984k in   4.994986s
          Time.parse     23.104k (±23.2%) i/s -    100.695k in   5.000834s

Comparison:
        Time.iso8601:   118351.6 i/s
          Time.parse:    23103.6 i/s - 5.12x  (± 0.00) slower

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
