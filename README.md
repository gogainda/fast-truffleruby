## Fast Truffle Ruby 


The idia of this project is to run all collected examples from the [Fast Ruby] (https://github.com/JuanitoFatas/fast-ruby) and run it against the latest truffle ruby version to see if the same results hold for the Truffle ruby. 

As you will see in the resalst below some results a quite different

## Results
```
truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       231.401M i/100ms
Function with splat arguments
                         1.497k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          2.290B (± 2.5%) i/s -     11.570B in   5.057181s
Function with splat arguments
                         14.940k (± 2.2%) i/s -     74.850k in   5.012835s

Comparison:
Function with single Array argument: 2289561715.0 i/s
Function with splat arguments:    14939.8 i/s - 153252.72x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment    42.827k i/100ms
Sequential Assignment
                       230.614M i/100ms
Calculating -------------------------------------
 Parallel Assignment      3.344B (±22.0%) i/s -     15.295B in   4.918957s
Sequential Assignment
                          2.291B (± 1.1%) i/s -     11.531B in   5.034095s

Comparison:
 Parallel Assignment: 3344426509.7 i/s
Sequential Assignment: 2290820597.4 i/s - 1.46x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter    53.037k i/100ms
       attr_accessor   230.082M i/100ms
Calculating -------------------------------------
   getter_and_setter      3.224B (±23.8%) i/s -     14.682B in   4.920952s
       attr_accessor      2.300B (± 0.9%) i/s -     11.504B in   5.001668s

Comparison:
   getter_and_setter: 3224208554.6 i/s
       attr_accessor: 2300247618.5 i/s - 1.40x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue     8.867k i/100ms
         respond_to?   231.127M i/100ms
Calculating -------------------------------------
      begin...rescue    101.159k (± 1.4%) i/s -    514.286k in   5.084961s
         respond_to?      2.292B (± 1.7%) i/s -     11.556B in   5.043511s

Comparison:
         respond_to?: 2291992167.6 i/s
      begin...rescue:   101158.8 i/s - 22657.37x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal    21.894k i/100ms
             &method   229.415M i/100ms
Calculating -------------------------------------
              normal      3.548B (±17.5%) i/s -     16.313B
             &method      2.289B (± 1.6%) i/s -     11.471B in   5.013289s

Comparison:
              normal: 3547542779.1 i/s
             &method: 2288650671.0 i/s - 1.55x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                        14.000  i/100ms
       define_method   287.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.393k (±25.1%) i/s -      4.522k in   5.001996s
       define_method      4.295k (±43.9%) i/s -     14.924k in   6.555762s

Comparison:
       define_method:     4294.5 i/s
module_eval with string:     1393.2 i/s - 3.08x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round     4.917k i/100ms
       Kernel#format    86.471k i/100ms
            String#%    87.351k i/100ms
Calculating -------------------------------------
         Float#round    667.721k (± 4.7%) i/s -      3.329M in   4.998267s
       Kernel#format    867.342k (± 1.7%) i/s -      4.410M in   5.086001s
            String#%    865.400k (± 1.3%) i/s -      4.368M in   5.047718s

Comparison:
       Kernel#format:   867342.3 i/s
            String#%:   865399.6 i/s - same-ish: difference falls within error
         Float#round:   667721.2 i/s - 1.30x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash    53.554k i/100ms
          OpenStruct   368.343M i/100ms
Calculating -------------------------------------
                Hash      3.216B (±23.9%) i/s -     14.639B in   4.918636s
          OpenStruct      3.671B (± 0.9%) i/s -     18.417B in   5.017048s

Comparison:
          OpenStruct: 3671223027.5 i/s
                Hash: 3216129061.7 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash    97.595k i/100ms
          OpenStruct   230.021M i/100ms
Calculating -------------------------------------
                Hash      2.579B (±23.5%) i/s -     12.062B in   4.929224s
          OpenStruct      2.292B (± 1.7%) i/s -     11.501B in   5.020388s

Comparison:
                Hash: 2579002298.2 i/s
          OpenStruct: 2291577044.1 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal    52.231k i/100ms
  ancestors.include?   185.448k i/100ms
Calculating -------------------------------------
  less than or equal     13.600M (± 6.0%) i/s -     67.639M in   4.997380s
  ancestors.include?      1.857M (± 1.3%) i/s -      9.458M in   5.092779s

Comparison:
  less than or equal: 13599518.9 i/s
  ancestors.include?:  1857412.3 i/s - 7.32x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     1.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     36.795  (± 2.7%) i/s -    184.000  in   5.001822s
         Kernel loop      9.389  (± 0.0%) i/s -     47.000  in   5.009074s

Comparison:
          While Loop:       36.8 i/s
         Kernel loop:        9.4 i/s - 3.92x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Ruby exception: E2MM#Raise
                       368.000  i/100ms
Ruby exception: Kernel#raise
                       229.265M i/100ms
Calculating -------------------------------------
Ruby exception: E2MM#Raise
                          8.330k (±17.4%) i/s -     39.744k in   5.001397s
Ruby exception: Kernel#raise
                          2.295B (± 1.0%) i/s -     11.693B in   5.095585s
Warming up --------------------------------------
Custom exception: E2MM#Raise
                       346.000  i/100ms
Custom exception: Kernel#raise
                       192.398M i/100ms
Calculating -------------------------------------
Custom exception: E2MM#Raise
                          9.358k (± 4.2%) i/s -     46.710k in   5.000755s
Custom exception: Kernel#raise
                          2.286B (± 3.0%) i/s -     11.544B in   5.056589s

Comparison:
Ruby exception: Kernel#raise: 2294852344.0 i/s
Ruby exception: E2MM#Raise:     8329.8 i/s - 275498.77x  (± 0.00) slower


Comparison:
Custom exception: Kernel#raise: 2285520721.2 i/s
Custom exception: E2MM#Raise:     9358.3 i/s - 244224.31x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   108.952k i/100ms
         Array#first   230.425M i/100ms
Calculating -------------------------------------
           Array#[0]      2.320B (± 9.6%) i/s -     11.236B in   4.930550s
         Array#first      2.288B (± 1.8%) i/s -     11.521B in   5.036754s

Comparison:
           Array#[0]: 2320469758.6 i/s
         Array#first: 2288206762.9 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   111.907k i/100ms
          Array#last   368.963M i/100ms
Calculating -------------------------------------
          Array#[-1]      3.708B (± 9.7%) i/s -     17.903B in   4.925278s
          Array#last      3.672B (± 0.8%) i/s -     18.448B in   5.024141s

Comparison:
          Array#[-1]: 3708146758.2 i/s
          Array#last: 3672156095.8 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   361.463k i/100ms
Calculating -------------------------------------
                find      0.106  (± 0.0%) i/s -      1.000  in   9.418270s
             bsearch      3.504M (±11.2%) i/s -     17.350M in   5.084879s

Comparison:
             bsearch:  3504273.2 i/s
                find:        0.1 i/s - 33004192.69x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.177  (± 0.0%) i/s -      1.000  in   5.664765s
        Array#insert      0.331  (± 0.0%) i/s -      2.000  in   6.045328s

Comparison:
        Array#insert:        0.3 i/s
       Array#unshift:        0.2 i/s - 1.87x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length    93.112k i/100ms
          Array#size   368.199M i/100ms
         Array#count   107.292M i/100ms
Calculating -------------------------------------
        Array#length      3.210B (±22.4%) i/s -     14.799B in   4.927808s
          Array#size      3.677B (± 1.1%) i/s -     18.410B in   5.007079s
         Array#count      1.092B (± 1.2%) i/s -      5.472B in   5.010557s

Comparison:
          Array#size: 3677262986.8 i/s
        Array#length: 3210180471.5 i/s - same-ish: difference falls within error
         Array#count: 1092240422.8 i/s - 3.37x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    71.000  i/100ms
        Array#sample     1.499M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    148.209k (± 8.9%) i/s -    720.508k in   4.991484s
        Array#sample     16.383M (± 0.8%) i/s -     82.441M in   5.032559s

Comparison:
        Array#sample: 16382524.8 i/s
 Array#shuffle.first:   148209.3 i/s - 110.54x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601   164.000  i/100ms
          Date.parse   545.000  i/100ms
Calculating -------------------------------------
        Date.iso8601     34.068k (±24.9%) i/s -    134.644k in   4.998956s
          Date.parse     37.836k (± 3.2%) i/s -    189.115k in   5.004018s

Comparison:
          Date.parse:    37836.4 i/s
        Date.iso8601:    34068.4 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push     1.290k i/100ms
           Array#map     1.120M i/100ms
Calculating -------------------------------------
   Array#each + push      3.144M (± 9.8%) i/s -     15.363M in   4.986178s
           Array#map     11.189M (± 1.0%) i/s -     56.007M in   5.006173s

Comparison:
           Array#map: 11188812.2 i/s
   Array#each + push:  3143804.2 i/s - 3.56x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop   836.992k i/100ms
               #each     1.037M i/100ms
Calculating -------------------------------------
            For loop      8.391M (± 0.9%) i/s -     42.687M in   5.087643s
               #each     10.300M (± 1.7%) i/s -     51.853M in   5.035836s

Comparison:
               #each: 10299873.1 i/s
            For loop:  8391006.6 i/s - 1.23x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop   403.755k i/100ms
     each_with_index   839.031k i/100ms
Calculating -------------------------------------
          While Loop      4.033M (± 1.1%) i/s -     20.188M in   5.006762s
     each_with_index      8.385M (± 0.6%) i/s -     41.952M in   5.003194s

Comparison:
     each_with_index:  8385261.7 i/s
          While Loop:  4032605.6 i/s - 2.08x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   226.364k i/100ms
      inject to_proc   224.854k i/100ms
        inject block   226.303k i/100ms
Calculating -------------------------------------
       inject symbol      2.251M (± 0.7%) i/s -     11.318M in   5.028043s
      inject to_proc      2.244M (± 3.1%) i/s -     11.243M in   5.016547s
        inject block      2.254M (± 1.1%) i/s -     11.315M in   5.021668s

Comparison:
        inject block:  2253558.8 i/s
       inject symbol:  2251129.2 i/s - same-ish: difference falls within error
      inject to_proc:  2243788.8 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)   342.000  i/100ms
   Array#map.flatten    18.635k i/100ms
      Array#flat_map    63.830k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    304.313k (±10.3%) i/s -      1.479M in   4.992997s
   Array#map.flatten    127.815k (± 2.1%) i/s -    652.225k in   5.105335s
      Array#flat_map    629.915k (± 3.4%) i/s -      3.192M in   5.073047s

Comparison:
      Array#flat_map:   629914.6 i/s
Array#map.flatten(1):   304312.9 i/s - 2.07x  (± 0.00) slower
   Array#map.flatten:   127815.5 i/s - 4.93x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   675.000  i/100ms
  Array#reverse_each   538.114k i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.246M (± 9.0%) i/s -     11.018M in   4.982143s
  Array#reverse_each      5.432M (± 0.8%) i/s -     27.444M in   5.052940s

Comparison:
  Array#reverse_each:  5431612.8 i/s
  Array#reverse.each:  2246211.5 i/s - 2.42x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       784.000  i/100ms
   Enumerable#detect     5.410M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                          5.430M (±10.5%) i/s -    105.346M in  19.892246s
   Enumerable#detect     54.103M (± 1.6%) i/s -      1.082B in  20.005000s

Comparison:
   Enumerable#detect: 54102771.3 i/s
Enumerable#select.first:  5429822.8 i/s - 9.96x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       586.000  i/100ms
Enumerable#select.last
                       329.629k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.526M (± 9.1%) i/s -     12.349M in   4.978289s
Enumerable#select.last
                          3.279M (± 1.2%) i/s -     16.481M in   5.027722s

Comparison:
Enumerable#select.last:  3278611.1 i/s
Enumerable#reverse.detect:  2525519.7 i/s - 1.30x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         3.606k i/100ms
  Enumerable#sort_by     2.937k i/100ms
     Enumerable#sort     4.677k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         66.579k (±14.7%) i/s -    292.086k in   5.031792s
  Enumerable#sort_by     34.969k (± 7.7%) i/s -    173.283k in   4.999641s
     Enumerable#sort     53.683k (± 1.6%) i/s -    271.266k in   5.054467s

Comparison:
Enumerable#sort_by (Symbol#to_proc):    66579.1 i/s
     Enumerable#sort:    53683.3 i/s - 1.24x  (± 0.00) slower
  Enumerable#sort_by:    34969.2 i/s - 1.90x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   346.000  i/100ms
Enumerable#sort_by...first
                        11.864k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      3.195M (± 9.2%) i/s -     15.643M in   4.968394s
Enumerable#sort_by...first
                        133.980k (± 3.3%) i/s -    676.248k in   5.054230s

Comparison:
   Enumerable#min_by:  3195371.9 i/s
Enumerable#sort_by...first:   133979.8 i/s - 23.85x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]    25.785k i/100ms
            Hash#dup   591.113k i/100ms
Calculating -------------------------------------
              Hash[]      5.857M (±11.1%) i/s -     28.183M in   4.995701s
            Hash#dup      5.893M (± 1.4%) i/s -     29.556M in   5.016101s

Comparison:
            Hash#dup:  5893266.3 i/s
              Hash[]:  5857072.0 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   123.683k i/100ms
  Hash#fetch, symbol   229.674M i/100ms
     Hash#[], string     9.582M i/100ms
  Hash#fetch, string     9.600M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      3.693B (±10.3%) i/s -     17.806B in   4.925620s
  Hash#fetch, symbol      2.298B (± 1.0%) i/s -     11.713B in   5.096777s
     Hash#[], string     99.929M (± 1.1%) i/s -    507.862M in   5.082810s
  Hash#fetch, string     92.278M (± 0.7%) i/s -    470.380M in   5.097681s

Comparison:
     Hash#[], symbol: 3693135815.1 i/s
  Hash#fetch, symbol: 2298448529.7 i/s - 1.61x  (± 0.00) slower
     Hash#[], string: 99929069.6 i/s - 36.96x  (± 0.00) slower
  Hash#fetch, string: 92277592.9 i/s - 40.02x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig     9.991k i/100ms
             Hash#[]     5.476M i/100ms
          Hash#[] ||     5.500M i/100ms
          Hash#[] &&   204.343k i/100ms
          Hash#fetch     3.180M i/100ms
 Hash#fetch fallback     3.116M i/100ms
Calculating -------------------------------------
            Hash#dig     10.055M (± 9.3%) i/s -     48.886M in   4.993223s
             Hash#[]     55.078M (± 2.2%) i/s -    279.252M in   5.072649s
          Hash#[] ||     55.414M (± 1.1%) i/s -    280.476M in   5.062006s
          Hash#[] &&     10.072M (± 3.8%) i/s -     50.473M in   5.018510s
          Hash#fetch     31.629M (± 1.2%) i/s -    158.990M in   5.027352s
 Hash#fetch fallback     30.460M (± 4.2%) i/s -    152.691M in   5.022152s

Comparison:
          Hash#[] ||: 55414385.5 i/s
             Hash#[]: 55077940.2 i/s - same-ish: difference falls within error
          Hash#fetch: 31629419.4 i/s - 1.75x  (± 0.00) slower
 Hash#fetch fallback: 30460225.0 i/s - 1.82x  (± 0.00) slower
          Hash#[] &&: 10072030.8 i/s - 5.50x  (± 0.00) slower
            Hash#dig: 10055093.5 i/s - 5.51x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const    49.914k i/100ms
  Hash#fetch + block   224.971M i/100ms
    Hash#fetch + arg   107.456M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      3.716B (± 9.8%) i/s -     17.816B in   4.916662s
  Hash#fetch + block      2.301B (± 0.8%) i/s -     11.698B in   5.085391s
    Hash#fetch + arg      1.091B (± 1.2%) i/s -      5.480B in   5.025465s

Comparison:
  Hash#fetch + const: 3716122047.2 i/s
  Hash#fetch + block: 2300546473.1 i/s - 1.62x  (± 0.00) slower
    Hash#fetch + arg: 1090649967.3 i/s - 3.41x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h   295.000  i/100ms
         sort + to_h   475.000  i/100ms
Calculating -------------------------------------
      sort_by + to_h    632.661k (±22.9%) i/s -      1.801M in   4.990569s
         sort + to_h     75.897k (± 6.6%) i/s -    377.150k in   5.002612s

Comparison:
      sort_by + to_h:   632661.4 i/s
         sort + to_h:    75897.0 i/s - 8.34x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each    11.454k i/100ms
       Hash#each_key     4.054M i/100ms
Calculating -------------------------------------
      Hash#keys.each     17.264M (± 8.5%) i/s -     85.057M in   4.990830s
       Hash#each_key     40.606M (± 1.3%) i/s -    206.767M in   5.092842s

Comparison:
       Hash#each_key: 40606290.5 i/s
      Hash#keys.each: 17264119.2 i/s - 2.35x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?   113.000  i/100ms
           Hash#key?     6.856M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      5.016k (±10.4%) i/s -     24.747k in   5.002147s
           Hash#key?     69.129M (± 1.1%) i/s -    349.643M in   5.058410s

Comparison:
           Hash#key?: 69129305.9 i/s
  Hash#keys.include?:     5016.1 i/s - 13781.47x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!   200.000  i/100ms
            Hash#[]=    57.056k i/100ms
Calculating -------------------------------------
         Hash#merge!    586.555k (±10.8%) i/s -      2.830M in   4.981624s
            Hash#[]=    564.812k (± 3.5%) i/s -      2.853M in   5.058532s

Comparison:
         Hash#merge!:   586554.9 i/s
            Hash#[]=:   564812.1 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                       190.000  i/100ms
      Hash#merge({})    18.336k i/100ms
 Hash#dup#merge!({})   175.000  i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        297.528k (±12.7%) i/s -      1.431M in   4.989704s
      Hash#merge({})    182.014k (± 7.5%) i/s -    916.800k in   5.095268s
 Hash#dup#merge!({})    289.801k (±11.7%) i/s -      1.401M in   4.990401s

Comparison:
{}#merge!(Hash) do end:   297528.4 i/s
 Hash#dup#merge!({}):   289801.2 i/s - same-ish: difference falls within error
      Hash#merge({}):   182014.0 i/s - 1.63x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other     5.396k i/100ms
          Hash#merge   231.199M i/100ms
Calculating -------------------------------------
        Hash#**other      2.319B (± 7.6%) i/s -     10.714B in   4.793581s
          Hash#merge      2.293B (± 1.4%) i/s -     11.560B in   5.042039s

Comparison:
        Hash#**other: 2318786694.1 i/s
          Hash#merge: 2293164298.2 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge    97.000  i/100ms
         Hash#merge!    58.037k i/100ms
Calculating -------------------------------------
          Hash#merge      9.381k (± 7.8%) i/s -     45.687k in   4.997438s
         Hash#merge!    576.211k (± 0.8%) i/s -      2.902M in   5.036437s

Comparison:
         Hash#merge!:   576211.3 i/s
          Hash#merge:     9380.9 i/s - 61.42x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice       26.091k i/100ms
Array#each               1.762M i/100ms
Array#each_w/_object     1.747M i/100ms
Hash#select-include      2.215M i/100ms
Calculating -------------------------------------
Hash#native-slice        21.510M (±10.4%) i/s -    105.382M in   4.993917s
Array#each               17.364M (± 3.7%) i/s -     88.077M in   5.081059s
Array#each_w/_object     17.444M (± 1.7%) i/s -     87.340M in   5.008426s
Hash#select-include      22.170M (± 3.8%) i/s -    110.740M in   5.004071s

Comparison:
Hash#select-include : 22170328.8 i/s
Hash#native-slice   : 21510011.1 i/s - same-ish: difference falls within error
Array#each_w/_object: 17444267.3 i/s - 1.27x  (± 0.00) slower
Array#each          : 17364380.0 i/s - 1.28x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?    76.000  i/100ms
         Hash#value?   186.000  i/100ms
Calculating -------------------------------------
Hash#values.include?      4.004k (±10.3%) i/s -     19.760k in   5.007287s
         Hash#value?     11.102k (± 4.5%) i/s -     55.428k in   5.002723s

Comparison:
         Hash#value?:    11102.4 i/s
Hash#values.include?:     4003.7 i/s - 2.77x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call    52.393k i/100ms
                send   231.139M i/100ms
      method_missing   106.745M i/100ms
Calculating -------------------------------------
                call      3.208B (±23.9%) i/s -     14.613B in   4.920663s
                send      2.300B (± 1.0%) i/s -     11.557B in   5.024711s
      method_missing      1.089B (± 1.4%) i/s -      5.551B in   5.097766s

Comparison:
                call: 3208393073.8 i/s
                send: 2300256356.0 i/s - 1.39x  (± 0.00) slower
      method_missing: 1089096506.2 i/s - 2.95x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    69.890k i/100ms
      Symbol#to_proc    68.973k i/100ms
Calculating -------------------------------------
               Block    700.678k (± 7.6%) i/s -      3.495M in   5.045588s
      Symbol#to_proc    689.336k (± 7.5%) i/s -      3.449M in   5.060129s

Comparison:
               Block:   700677.7 i/s
      Symbol#to_proc:   689336.4 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   366.105M i/100ms
       block + yield   369.602M i/100ms
        unused block   100.048M i/100ms
               yield   106.731M i/100ms
Calculating -------------------------------------
          block.call      3.671B (± 1.5%) i/s -     18.671B in   5.087846s
       block + yield      3.670B (± 1.0%) i/s -     18.480B in   5.036177s
        unused block      1.090B (± 1.1%) i/s -      5.503B in   5.047412s
               yield      1.085B (± 1.7%) i/s -      5.443B in   5.019094s

Comparison:
          block.call: 3670666883.3 i/s
       block + yield: 3669877970.5 i/s - same-ish: difference falls within error
        unused block: 1090313285.3 i/s - 3.37x  (± 0.00) slower
               yield: 1084848709.4 i/s - 3.38x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?     4.678k i/100ms
      range#include?     8.250k i/100ms
       range#member?     9.058k i/100ms
       plain compare   368.834M i/100ms
Calculating -------------------------------------
        range#cover?      1.564B (±86.3%) i/s -      1.252B in   4.898824s
      range#include?    162.111k (± 2.1%) i/s -    816.750k in   5.040367s
       range#member?    172.713k (± 2.4%) i/s -    869.568k in   5.037645s
       plain compare      3.675B (± 1.5%) i/s -     18.442B in   5.018873s

Comparison:
       plain compare: 3675303880.5 i/s
        range#cover?: 1564394382.3 i/s - 2.35x  (± 0.00) slower
       range#member?:   172712.8 i/s - 21279.86x  (± 0.00) slower
      range#include?:   162111.0 i/s - 22671.52x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?    27.366k i/100ms
           String#=~   292.626k i/100ms
          Regexp#===   288.452k i/100ms
        String#match   111.177k i/100ms
Calculating -------------------------------------
       String#match?     16.964M (±10.3%) i/s -     83.302M in   4.994981s
           String#=~      2.894M (± 1.2%) i/s -     14.631M in   5.056935s
          Regexp#===      2.823M (± 1.1%) i/s -     14.134M in   5.007097s
        String#match      1.098M (± 3.3%) i/s -      5.559M in   5.068561s

Comparison:
       String#match?: 16964191.0 i/s
           String#=~:  2893728.9 i/s - 5.86x  (± 0.00) slower
          Regexp#===:  2823142.5 i/s - 6.01x  (± 0.00) slower
        String#match:  1098199.8 i/s - 15.45x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==    20.502k i/100ms
      String#casecmp     4.881M i/100ms
Calculating -------------------------------------
String#downcase + ==     26.221M (±10.4%) i/s -    128.199M in   4.991925s
      String#casecmp     49.046M (± 0.7%) i/s -    248.926M in   5.075582s

Comparison:
      String#casecmp: 49046412.8 i/s
String#downcase + ==: 26221221.4 i/s - 1.87x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   110.367k i/100ms
       String#concat   231.570M i/100ms
       String#append   107.471M i/100ms
         "foo" "bar"   106.729M i/100ms
  "#{'foo'}#{'bar'}"   106.041M i/100ms
Calculating -------------------------------------
            String#+      2.332B (±11.3%) i/s -     11.256B in   4.928450s
       String#concat      2.305B (± 1.0%) i/s -     11.578B in   5.024003s
       String#append      1.086B (± 2.1%) i/s -      5.481B in   5.051108s
         "foo" "bar"      1.093B (± 1.1%) i/s -      5.550B in   5.080431s
  "#{'foo'}#{'bar'}"      1.092B (± 0.9%) i/s -      5.514B in   5.052156s

Comparison:
            String#+: 2331845138.0 i/s
       String#concat: 2304872503.6 i/s - same-ish: difference falls within error
         "foo" "bar": 1092542818.3 i/s - 2.13x  (± 0.00) slower
  "#{'foo'}#{'bar'}": 1091523853.2 i/s - 2.14x  (± 0.00) slower
       String#append: 1085631647.7 i/s - 2.15x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@    45.425k i/100ms
          String#dup   229.343M i/100ms
Calculating -------------------------------------
           String#+@      3.730B (± 9.3%) i/s -     17.919B in   4.916371s
          String#dup      2.293B (± 2.0%) i/s -     11.467B in   5.003608s

Comparison:
           String#+@: 3729539634.7 i/s
          String#dup: 2292711048.8 i/s - 1.63x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~    10.357k i/100ms
       String#match?   254.579k i/100ms
    String#end_with?     1.112M i/100ms
Calculating -------------------------------------
           String#=~      1.393M (± 4.0%) i/s -      6.950M in   4.999663s
       String#match?      2.552M (± 1.4%) i/s -     12.984M in   5.087852s
    String#end_with?     11.033M (± 3.4%) i/s -     55.617M in   5.047836s

Comparison:
    String#end_with?: 11032733.0 i/s
       String#match?:  2552346.4 i/s - 4.32x  (± 0.00) slower
           String#=~:  1392526.3 i/s - 7.92x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub     2.577k i/100ms
          String#sub    49.386k i/100ms
String#dup["string"]=
                         2.191M i/100ms
Calculating -------------------------------------
         String#gsub    783.351k (± 5.5%) i/s -      3.899M in   4.998011s
          String#sub    498.163k (± 1.0%) i/s -      2.519M in   5.056421s
String#dup["string"]=
                         22.355M (± 1.5%) i/s -    111.761M in   5.000452s

Comparison:
String#dup["string"]=: 22355075.3 i/s
         String#gsub:   783351.3 i/s - 28.54x  (± 0.00) slower
          String#sub:   498163.4 i/s - 44.87x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub     2.551k i/100ms
           String#tr   302.746k i/100ms
Calculating -------------------------------------
         String#gsub      1.696M (± 9.7%) i/s -      8.339M in   4.993987s
           String#tr      2.973M (± 1.5%) i/s -     15.137M in   5.092321s

Comparison:
           String#tr:  2973309.0 i/s
         String#gsub:  1696112.7 i/s - 1.75x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze    94.345k i/100ms
         With Freeze   231.193M i/100ms
Calculating -------------------------------------
      Without Freeze      2.630B (±24.6%) i/s -     12.220B in   4.928637s
         With Freeze      2.287B (± 2.6%) i/s -     11.560B in   5.057928s

Comparison:
      Without Freeze: 2630190032.7 i/s
         With Freeze: 2287213267.8 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/    78.000  i/100ms
      String#squeeze    65.073k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/     41.944k (± 9.6%) i/s -    206.622k in   4.994226s
      String#squeeze    646.704k (± 2.4%) i/s -      3.254M in   5.034288s

Comparison:
      String#squeeze:   646704.0 i/s
 String#gsub/regex+/:    41944.5 i/s - 15.42x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~   225.806k i/100ms
       String#match?     1.059M i/100ms
  String#start_with?     3.057M i/100ms
Calculating -------------------------------------
           String#=~      2.361M (± 2.8%) i/s -     11.968M in   5.072684s
       String#match?     10.594M (± 1.0%) i/s -     54.001M in   5.097651s
  String#start_with?     30.177M (± 1.7%) i/s -    152.852M in   5.066640s

Comparison:
  String#start_with?: 30177080.8 i/s
       String#match?: 10594257.0 i/s - 2.85x  (± 0.00) slower
           String#=~:  2361409.5 i/s - 12.78x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?     4.211k i/100ms
    String#[0, n] ==   364.080k i/100ms
   String#[RANGE] ==    23.463k i/100ms
   String#[0...n] ==   303.052k i/100ms
Calculating -------------------------------------
  String#start_with?      4.697M (±11.3%) i/s -     22.651M in   4.992611s
    String#[0, n] ==      3.477M (± 6.4%) i/s -     17.476M in   5.056245s
   String#[RANGE] ==      3.873M (± 7.2%) i/s -     19.263M in   5.003404s
   String#[0...n] ==      2.975M (± 1.8%) i/s -     15.153M in   5.094987s

Comparison:
  String#start_with?:  4697247.9 i/s
   String#[RANGE] ==:  3873420.7 i/s - 1.21x  (± 0.00) slower
    String#[0, n] ==:  3476554.0 i/s - 1.35x  (± 0.00) slower
   String#[0...n] ==:  2975017.7 i/s - 1.58x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=     9.934k i/100ms
 String#sub!'string'    73.383k i/100ms
String#gsub!'string'    56.418k i/100ms
  String#[/regexp/]=   345.274k i/100ms
 String#sub!/regexp/   203.681k i/100ms
String#gsub!/regexp/   139.048k i/100ms
Calculating -------------------------------------
  String#['string']=    106.844M (±10.7%) i/s -    506.455M in   4.962401s
 String#sub!'string'    722.851k (± 2.1%) i/s -      3.669M in   5.078434s
String#gsub!'string'    757.454k (± 2.0%) i/s -      3.836M in   5.067026s
  String#[/regexp/]=      3.493M (± 1.4%) i/s -     17.609M in   5.042810s
 String#sub!/regexp/      2.004M (± 1.6%) i/s -     10.184M in   5.083816s
String#gsub!/regexp/      1.438M (± 0.9%) i/s -      7.230M in   5.028119s

Comparison:
  String#['string']=: 106843724.3 i/s
  String#[/regexp/]=:  3492602.9 i/s - 30.59x  (± 0.00) slower
 String#sub!/regexp/:  2003730.0 i/s - 53.32x  (± 0.00) slower
String#gsub!/regexp/:  1438134.1 i/s - 74.29x  (± 0.00) slower
String#gsub!'string':   757454.5 i/s - 141.06x  (± 0.00) slower
 String#sub!'string':   722851.0 i/s - 147.81x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub     4.748k i/100ms
        String#chomp     2.630M i/100ms
String#delete_suffix     2.687M i/100ms
Calculating -------------------------------------
          String#sub      1.001M (± 5.4%) i/s -      4.985M in   4.998669s
        String#chomp     25.997M (± 1.9%) i/s -    131.477M in   5.059253s
String#delete_suffix     26.612M (± 1.6%) i/s -    134.355M in   5.050068s

Comparison:
String#delete_suffix: 26611532.0 i/s
        String#chomp: 25996819.4 i/s - same-ish: difference falls within error
          String#sub:  1000821.8 i/s - 26.59x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     6.032k i/100ms
          String#sub   100.680k i/100ms
Calculating -------------------------------------
String#delete_prefix     28.821M (±10.9%) i/s -    139.321M in   4.977043s
          String#sub      1.007M (± 1.2%) i/s -      5.135M in   5.099253s

Comparison:
String#delete_prefix: 28821459.2 i/s
          String#sub:  1007105.2 i/s - 28.62x  (± 0.00) slower

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     2.355M i/100ms
    String#unpack[0]     2.383M i/100ms
Calculating -------------------------------------
      String#unpack1     23.608M (± 1.2%) i/s -    120.105M in   5.088357s
    String#unpack[0]     23.763M (± 0.8%) i/s -    119.143M in   5.014142s

Comparison:
    String#unpack[0]: 23762829.6 i/s
      String#unpack1: 23607660.5 i/s - same-ish: difference falls within error

truffleruby 20.3.0-dev-cc7f184c, like ruby 2.6.6, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601     1.296k i/100ms
          Time.parse   387.000  i/100ms
Calculating -------------------------------------
        Time.iso8601    170.766k (± 8.9%) i/s -    835.920k in   4.999516s
          Time.parse     29.909k (± 3.4%) i/s -    149.382k in   5.001061s

Comparison:
        Time.iso8601:   170766.4 i/s
          Time.parse:    29908.7 i/s - 5.71x  (± 0.00) slower

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
