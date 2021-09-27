## Fast TruffleRuby 


The idea of this project is to run all collected examples from [Fast Ruby](https://github.com/JuanitoFatas/fast-ruby) and run it against the latest TruffleRuby version to see if the same results hold for TruffleRuby.

As you will see in the results below, some results a quite different
## Scheduled run results
There is a Github Action workflow configured to run the test suit periodically and save the results into [runs.log](https://github.com/gogainda/fast-truffleruby/blob/master/runs.log) file


## Results 
```
$ ruby -v code/general/attr-accessor-vs-getter-and-setter.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   getter_and_setter   207.832M i/100ms
       attr_accessor   337.694M i/100ms
Calculating -------------------------------------
   getter_and_setter      2.085B (± 4.4%) i/s -     10.599B in   5.094289s
       attr_accessor      3.356B (± 3.1%) i/s -     16.885B in   5.035839s

Comparison:
       attr_accessor: 3356206542.9 i/s
   getter_and_setter: 2085044925.0 i/s - 1.61x  (± 0.00) slower

$ ruby -v code/general/raise-vs-e2mmap.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
$ ruby -v code/general/array-argument-vs-splat-arguments.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Function with single Array argument
                       213.130M i/100ms
Function with splat arguments
                         1.474k i/100ms
Calculating -------------------------------------
Function with single Array argument
                          2.111B (± 2.9%) i/s -     10.656B in   5.052069s
Function with splat arguments
                         14.426k (± 4.3%) i/s -     72.226k in   5.016355s

Comparison:
Function with single Array argument: 2111188056.7 i/s
Function with splat arguments:    14426.2 i/s - 146344.26x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   200.426M i/100ms
          OpenStruct   321.360M i/100ms
Calculating -------------------------------------
                Hash      2.123B (± 2.1%) i/s -     10.623B in   5.006760s
          OpenStruct      3.227B (± 5.0%) i/s -     16.389B in   5.091879s

Comparison:
          OpenStruct: 3227068839.9 i/s
                Hash: 2122639600.1 i/s - 1.52x  (± 0.00) slower

$ ruby -v code/general/loop-vs-while-true.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     1.000  i/100ms
         Kernel loop     1.000  i/100ms
Calculating -------------------------------------
          While Loop     33.032  (± 6.1%) i/s -    165.000  in   5.011669s
         Kernel loop      8.071  (± 0.0%) i/s -     41.000  in   5.084945s

Comparison:
          While Loop:       33.0 i/s
         Kernel loop:        8.1 i/s - 4.09x  (± 0.00) slower

$ ruby -v code/general/inheritance-check.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  less than or equal     1.150M i/100ms
  ancestors.include?   178.303k i/100ms
Calculating -------------------------------------
  less than or equal     12.135M (± 4.4%) i/s -     60.967M in   5.034657s
  ancestors.include?      1.803M (± 4.1%) i/s -      9.093M in   5.052257s

Comparison:
  less than or equal: 12135387.2 i/s
  ancestors.include?:  1803204.1 i/s - 6.73x  (± 0.00) slower

$ ruby -v code/general/assignment.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Parallel Assignment   207.747M i/100ms
Sequential Assignment
                       215.275M i/100ms
Calculating -------------------------------------
 Parallel Assignment      2.109B (± 2.7%) i/s -     10.595B in   5.026603s
Sequential Assignment
                          2.107B (± 2.4%) i/s -     10.548B in   5.009823s

Comparison:
 Parallel Assignment: 2109416753.3 i/s
Sequential Assignment: 2106761597.8 i/s - same-ish: difference falls within error

$ ruby -v code/general/format-vs-round-and-to-s.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Float#round    49.706k i/100ms
       Kernel#format    74.579k i/100ms
            String#%    73.723k i/100ms
Calculating -------------------------------------
         Float#round    555.257k (± 2.8%) i/s -      2.784M in   5.017011s
       Kernel#format    732.875k (± 4.1%) i/s -      3.729M in   5.097216s
            String#%    727.396k (± 4.7%) i/s -      3.686M in   5.079658s

Comparison:
       Kernel#format:   732875.0 i/s
            String#%:   727395.6 i/s - same-ish: difference falls within error
         Float#round:   555257.2 i/s - 1.32x  (± 0.00) slower

$ ruby -v code/general/block-apply-method.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              normal   205.596M i/100ms
             &method   332.676M i/100ms
Calculating -------------------------------------
              normal      2.084B (± 4.0%) i/s -     10.485B in   5.040524s
             &method      3.333B (± 4.8%) i/s -     16.634B in   5.003343s

Comparison:
             &method: 3333327072.7 i/s
              normal: 2083755174.7 i/s - 1.60x  (± 0.00) slower

$ ruby -v code/general/define_method-vs-module-eval.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
module_eval with string
                       224.000  i/100ms
       define_method   141.000  i/100ms
Calculating -------------------------------------
module_eval with string
                          1.850k (±40.5%) i/s -      7.168k in   5.753534s
       define_method      3.896k (±33.6%) i/s -     14.523k in   5.025308s

Comparison:
       define_method:     3896.3 i/s
module_eval with string:     1850.0 i/s - same-ish: difference falls within error

$ ruby -v code/general/begin-rescue-vs-respond-to.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      begin...rescue    10.022k i/100ms
         respond_to?   206.353M i/100ms
Calculating -------------------------------------
      begin...rescue    105.573k (± 3.1%) i/s -    531.166k in   5.036300s
         respond_to?      2.109B (± 3.4%) i/s -     10.730B in   5.093218s

Comparison:
         respond_to?: 2109471786.8 i/s
      begin...rescue:   105572.9 i/s - 19981.19x  (± 0.00) slower

$ ruby -v code/general/hash-vs-openstruct-on-access.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                Hash   199.148M i/100ms
          OpenStruct    72.169M i/100ms
Calculating -------------------------------------
                Hash      2.116B (± 2.5%) i/s -     10.754B in   5.085503s
          OpenStruct    705.181M (± 3.1%) i/s -      3.536B in   5.019742s

Comparison:
                Hash: 2115947061.6 i/s
          OpenStruct: 705180947.9 i/s - 3.00x  (± 0.00) slower

$ ruby -v code/hash/bracket-vs-dup.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
              Hash[]   548.878k i/100ms
            Hash#dup   591.498k i/100ms
Calculating -------------------------------------
              Hash[]      5.850M (± 6.1%) i/s -     29.639M in   5.086837s
            Hash#dup      5.734M (± 4.5%) i/s -     28.983M in   5.065355s

Comparison:
              Hash[]:  5850042.8 i/s
            Hash#dup:  5734370.2 i/s - same-ish: difference falls within error

$ ruby -v code/hash/values-include-vs-value.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#values.include?   401.000  i/100ms
         Hash#value?   264.897k i/100ms
Calculating -------------------------------------
Hash#values.include?      4.585k (±10.1%) i/s -     22.857k in   5.038528s
         Hash#value?      2.457M (± 2.6%) i/s -     12.450M in   5.070101s

Comparison:
         Hash#value?:  2457250.4 i/s
Hash#values.include?:     4585.3 i/s - 535.90x  (± 0.00) slower

$ ruby -v code/hash/dig-vs-[]-vs-fetch.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            Hash#dig    70.496M i/100ms
             Hash#[]    84.600M i/100ms
          Hash#[] ||    85.994M i/100ms
          Hash#[] &&    86.541M i/100ms
          Hash#fetch    86.210M i/100ms
 Hash#fetch fallback    87.071M i/100ms
Calculating -------------------------------------
            Hash#dig    839.979M (± 3.1%) i/s -      4.230B in   5.040715s
             Hash#[]    844.023M (± 2.7%) i/s -      4.230B in   5.015570s
          Hash#[] ||    847.400M (± 2.6%) i/s -      4.300B in   5.077463s
          Hash#[] &&    839.039M (± 3.2%) i/s -      4.241B in   5.059332s
          Hash#fetch    835.506M (± 4.3%) i/s -      4.224B in   5.065925s
 Hash#fetch fallback    840.886M (± 3.8%) i/s -      4.266B in   5.082061s

Comparison:
          Hash#[] ||: 847400332.4 i/s
             Hash#[]: 844022627.6 i/s - same-ish: difference falls within error
 Hash#fetch fallback: 840885624.8 i/s - same-ish: difference falls within error
            Hash#dig: 839979376.7 i/s - same-ish: difference falls within error
          Hash#[] &&: 839038996.9 i/s - same-ish: difference falls within error
          Hash#fetch: 835506331.0 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-bang-vs-merge-vs-dup-merge-bang.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
{}#merge!(Hash) do end
                        21.612k i/100ms
      Hash#merge({})    17.188k i/100ms
 Hash#dup#merge!({})    26.203k i/100ms
Calculating -------------------------------------
{}#merge!(Hash) do end
                        308.538k (± 3.3%) i/s -      1.556M in   5.049026s
      Hash#merge({})    166.837k (± 4.9%) i/s -    842.212k in   5.061275s
 Hash#dup#merge!({})    257.557k (± 3.9%) i/s -      1.310M in   5.095571s

Comparison:
{}#merge!(Hash) do end:   308537.9 i/s
 Hash#dup#merge!({}):   257557.3 i/s - 1.20x  (± 0.00) slower
      Hash#merge({}):   166837.0 i/s - 1.85x  (± 0.00) slower

$ ruby -v code/hash/slice-native-vs-before-native.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Hash#native-slice        1.598M i/100ms
Array#each               1.449M i/100ms
Array#each_w/_object     1.435M i/100ms
Hash#select-include      1.878M i/100ms
Calculating -------------------------------------
Hash#native-slice        18.385M (± 2.8%) i/s -     92.694M in   5.046007s
Array#each               14.410M (± 3.5%) i/s -     72.447M in   5.033968s
Array#each_w/_object     14.418M (± 2.7%) i/s -     73.177M in   5.079178s
Hash#select-include      18.164M (± 3.0%) i/s -     92.020M in   5.070895s

Comparison:
Hash#native-slice   : 18384999.2 i/s
Hash#select-include : 18163800.3 i/s - same-ish: difference falls within error
Array#each_w/_object: 14418058.4 i/s - 1.28x  (± 0.00) slower
Array#each          : 14409773.3 i/s - 1.28x  (± 0.00) slower

$ ruby -v code/hash/keys-include-vs-key.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#keys.include?   247.000  i/100ms
           Hash#key?    47.511M i/100ms
Calculating -------------------------------------
  Hash#keys.include?      3.426k (± 8.9%) i/s -     17.043k in   5.018258s
           Hash#key?    467.822M (± 2.7%) i/s -      2.376B in   5.081575s

Comparison:
           Hash#key?: 467821860.0 i/s
  Hash#keys.include?:     3425.8 i/s - 136557.43x  (± 0.00) slower

$ ruby -v code/hash/hash-key-sort_by-vs-sort.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      sort_by + to_h    27.895k i/100ms
         sort + to_h     7.591k i/100ms
Calculating -------------------------------------
      sort_by + to_h    353.571k (±16.0%) i/s -      1.729M in   5.044517s
         sort + to_h     95.531k (± 3.8%) i/s -    478.233k in   5.014006s

Comparison:
      sort_by + to_h:   353570.6 i/s
         sort + to_h:    95530.9 i/s - 3.70x  (± 0.00) slower

$ ruby -v code/hash/merge-vs-merge-bang.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Hash#merge   708.000  i/100ms
         Hash#merge!    47.550k i/100ms
Calculating -------------------------------------
          Hash#merge      9.071k (± 3.9%) i/s -     45.312k in   5.003265s
         Hash#merge!    478.594k (± 5.0%) i/s -      2.425M in   5.080589s

Comparison:
         Hash#merge!:   478594.4 i/s
          Hash#merge:     9071.1 i/s - 52.76x  (± 0.00) slower

$ ruby -v code/hash/fetch-vs-fetch-with-block.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Hash#fetch + const   332.203M i/100ms
  Hash#fetch + block   334.679M i/100ms
    Hash#fetch + arg   339.983M i/100ms
Calculating -------------------------------------
  Hash#fetch + const      3.375B (± 2.8%) i/s -     16.942B in   5.023353s
  Hash#fetch + block      3.329B (± 4.8%) i/s -     16.734B in   5.040873s
    Hash#fetch + arg      3.361B (± 3.3%) i/s -     16.999B in   5.063162s

Comparison:
  Hash#fetch + const: 3375435424.7 i/s
    Hash#fetch + arg: 3361457947.4 i/s - same-ish: difference falls within error
  Hash#fetch + block: 3328688018.1 i/s - same-ish: difference falls within error

$ ruby -v code/hash/bracket-vs-fetch.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
     Hash#[], symbol   210.104M i/100ms
  Hash#fetch, symbol   341.564M i/100ms
     Hash#[], string     7.340M i/100ms
  Hash#fetch, string     6.702M i/100ms
Calculating -------------------------------------
     Hash#[], symbol      2.094B (± 2.9%) i/s -     10.505B in   5.021701s
  Hash#fetch, symbol      3.353B (± 4.0%) i/s -     16.737B in   5.000820s
     Hash#[], string     68.712M (± 4.1%) i/s -    344.974M in   5.029338s
  Hash#fetch, string     64.793M (± 3.4%) i/s -    328.399M in   5.074515s

Comparison:
  Hash#fetch, symbol: 3352677218.6 i/s
     Hash#[], symbol: 2093748841.3 i/s - 1.60x  (± 0.00) slower
     Hash#[], string: 68712486.3 i/s - 48.79x  (± 0.00) slower
  Hash#fetch, string: 64793281.0 i/s - 51.74x  (± 0.00) slower

$ ruby -v code/hash/keys-each-vs-each_key.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Hash#keys.each   179.127k i/100ms
       Hash#each_key   208.856k i/100ms
Calculating -------------------------------------
      Hash#keys.each      1.913M (± 3.3%) i/s -      9.673M in   5.061389s
       Hash#each_key      2.111M (± 3.2%) i/s -     10.652M in   5.050705s

Comparison:
       Hash#each_key:  2111208.4 i/s
      Hash#keys.each:  1913266.0 i/s - 1.10x  (± 0.00) slower

$ ruby -v code/hash/merge-bang-vs-[]=.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         Hash#merge!    40.749k i/100ms
            Hash#[]=    53.827k i/100ms
Calculating -------------------------------------
         Hash#merge!    502.246k (± 5.8%) i/s -      2.526M in   5.049220s
            Hash#[]=    530.601k (± 4.5%) i/s -      2.691M in   5.083526s

Comparison:
            Hash#[]=:   530601.4 i/s
         Hash#merge!:   502246.3 i/s - same-ish: difference falls within error

$ ruby -v code/hash/merge-vs-double-splat-operator.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Hash#**other   211.991M i/100ms
          Hash#merge   342.173M i/100ms
Calculating -------------------------------------
        Hash#**other      2.109B (± 2.9%) i/s -     10.600B in   5.031240s
          Hash#merge      3.288B (± 3.9%) i/s -     16.424B in   5.002213s

Comparison:
          Hash#merge: 3288466425.3 i/s
        Hash#**other: 2108511019.1 i/s - 1.56x  (± 0.00) slower

$ ruby -v code/array/length-vs-size-vs-count.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Array#length   203.938M i/100ms
          Array#size   216.388M i/100ms
         Array#count   208.615M i/100ms
Calculating -------------------------------------
        Array#length      2.089B (± 4.0%) i/s -     10.605B in   5.084698s
          Array#size      2.088B (± 3.9%) i/s -     10.603B in   5.087264s
         Array#count      2.099B (± 3.1%) i/s -     10.639B in   5.072642s

Comparison:
         Array#count: 2099482566.0 i/s
        Array#length: 2089216121.3 i/s - same-ish: difference falls within error
          Array#size: 2087583916.8 i/s - same-ish: difference falls within error

$ ruby -v code/array/shuffle-first-vs-sample.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 Array#shuffle.first    31.828k i/100ms
        Array#sample     3.632M i/100ms
Calculating -------------------------------------
 Array#shuffle.first    349.711k (± 3.0%) i/s -      1.751M in   5.010344s
        Array#sample     36.049M (± 3.9%) i/s -    181.595M in   5.045950s

Comparison:
        Array#sample: 36048903.9 i/s
 Array#shuffle.first:   349710.7 i/s - 103.08x  (± 0.00) slower

$ ruby -v code/array/bsearch-vs-find.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                find     1.000  i/100ms
             bsearch   422.318k i/100ms
Calculating -------------------------------------
                find      0.108  (± 0.0%) i/s -      1.000  in   9.273907s
             bsearch      4.171M (± 8.9%) i/s -     20.694M in   5.026876s

Comparison:
             bsearch:  4170851.7 i/s
                find:        0.1 i/s - 38680088.78x  (± 0.00) slower

$ ruby -v code/array/array-first-vs-index.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           Array#[0]   331.475M i/100ms
         Array#first   330.241M i/100ms
Calculating -------------------------------------
           Array#[0]      3.400B (± 2.3%) i/s -     17.237B in   5.073100s
         Array#first      3.370B (± 3.0%) i/s -     16.842B in   5.003062s

Comparison:
           Array#[0]: 3399509611.4 i/s
         Array#first: 3369596908.6 i/s - same-ish: difference falls within error

$ ruby -v code/array/array-last-vs-index.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          Array#[-1]   209.141M i/100ms
          Array#last   191.105M i/100ms
Calculating -------------------------------------
          Array#[-1]      2.095B (± 3.0%) i/s -     10.666B in   5.095125s
          Array#last      2.108B (± 3.1%) i/s -     10.702B in   5.082674s

Comparison:
          Array#last: 2107657282.9 i/s
          Array#[-1]: 2095403645.5 i/s - same-ish: difference falls within error

$ ruby -v code/array/insert-vs-unshift.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       Array#unshift     1.000  i/100ms
        Array#insert     1.000  i/100ms
Calculating -------------------------------------
       Array#unshift      0.176  (± 0.0%) i/s -      1.000  in   5.696643s
        Array#insert      1.266  (± 0.0%) i/s -      7.000  in   5.530197s

Comparison:
        Array#insert:        1.3 i/s
       Array#unshift:        0.2 i/s - 7.21x  (± 0.00) slower

$ ruby -v code/date/iso8601-vs-parse.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Date.iso8601   992.000  i/100ms
          Date.parse    98.000  i/100ms
Calculating -------------------------------------
        Date.iso8601     28.665k (±35.3%) i/s -     95.232k in   5.005437s
          Date.parse      8.936k (±18.5%) i/s -     36.750k in   5.000432s

Comparison:
        Date.iso8601:    28664.7 i/s
          Date.parse:     8935.5 i/s - 3.21x  (± 0.00) slower

$ ruby -v code/enumerable/reverse-each-vs-reverse_each.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  Array#reverse.each   230.367k i/100ms
  Array#reverse_each     1.816M i/100ms
Calculating -------------------------------------
  Array#reverse.each      2.496M (± 3.0%) i/s -     12.670M in   5.081466s
  Array#reverse_each     18.633M (± 2.7%) i/s -     94.415M in   5.071097s

Comparison:
  Array#reverse_each: 18632847.3 i/s
  Array#reverse.each:  2495770.3 i/s - 7.47x  (± 0.00) slower

$ ruby -v code/enumerable/inject-symbol-vs-block.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       inject symbol   226.393k i/100ms
      inject to_proc   238.418k i/100ms
        inject block   238.067k i/100ms
Calculating -------------------------------------
       inject symbol      2.327M (± 5.5%) i/s -     11.772M in   5.076516s
      inject to_proc      2.397M (± 2.7%) i/s -     12.159M in   5.076487s
        inject block      2.391M (± 2.6%) i/s -     12.141M in   5.082027s

Comparison:
      inject to_proc:  2396993.6 i/s
        inject block:  2390754.8 i/s - same-ish: difference falls within error
       inject symbol:  2326527.0 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/sort-vs-sort_by.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         3.906k i/100ms
  Enumerable#sort_by     4.423k i/100ms
     Enumerable#sort     2.921k i/100ms
Calculating -------------------------------------
Enumerable#sort_by (Symbol#to_proc)
                         48.174k (±14.5%) i/s -    226.548k in   5.055621s
  Enumerable#sort_by     48.927k (±13.5%) i/s -    238.842k in   5.043419s
     Enumerable#sort     69.419k (± 4.8%) i/s -    347.599k in   5.019633s

Comparison:
     Enumerable#sort:    69419.2 i/s
  Enumerable#sort_by:    48927.1 i/s - 1.42x  (± 0.00) slower
Enumerable#sort_by (Symbol#to_proc):    48174.4 i/s - 1.44x  (± 0.00) slower

$ ruby -v code/enumerable/each-vs-for-loop.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            For loop    13.551M i/100ms
               #each    17.852M i/100ms
Calculating -------------------------------------
            For loop    141.592M (± 2.4%) i/s -    718.215M in   5.075356s
               #each    175.892M (± 3.6%) i/s -    892.583M in   5.081763s

Comparison:
               #each: 175892229.7 i/s
            For loop: 141591895.5 i/s - 1.24x  (± 0.00) slower

$ ruby -v code/enumerable/sort_by-first-vs-min_by.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Enumerable#min_by   407.392k i/100ms
Enumerable#sort_by...first
                         8.913k i/100ms
Calculating -------------------------------------
   Enumerable#min_by      4.010M (± 5.4%) i/s -     20.370M in   5.095652s
Enumerable#sort_by...first
                        107.304k (± 2.9%) i/s -    543.693k in   5.071214s

Comparison:
   Enumerable#min_by:  4010218.9 i/s
Enumerable#sort_by...first:   107304.0 i/s - 37.37x  (± 0.00) slower

$ ruby -v code/enumerable/each_with_index-vs-while-loop.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          While Loop     1.289M i/100ms
     each_with_index     1.266M i/100ms
Calculating -------------------------------------
          While Loop     12.489M (± 4.5%) i/s -     63.168M in   5.068141s
     each_with_index     12.569M (± 4.2%) i/s -     63.285M in   5.044142s

Comparison:
     each_with_index: 12569315.5 i/s
          While Loop: 12489349.8 i/s - same-ish: difference falls within error

$ ruby -v code/enumerable/select-first-vs-detect.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#select.first
                       952.254k i/100ms
   Enumerable#detect     5.874M i/100ms
Calculating -------------------------------------
Enumerable#select.first
                         10.565M (± 3.3%) i/s -    211.400M in  20.032619s
   Enumerable#detect     59.361M (± 3.5%) i/s -      1.187B in  20.016642s

Comparison:
   Enumerable#detect: 59360779.5 i/s
Enumerable#select.first: 10564638.3 i/s - 5.62x  (± 0.00) slower

$ ruby -v code/enumerable/select-last-vs-reverse-detect.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Enumerable#reverse.detect
                       252.619k i/100ms
Enumerable#select.last
                       519.612k i/100ms
Calculating -------------------------------------
Enumerable#reverse.detect
                          2.650M (± 4.8%) i/s -     13.389M in   5.065287s
Enumerable#select.last
                          5.124M (± 3.3%) i/s -     25.981M in   5.075773s

Comparison:
Enumerable#select.last:  5124160.8 i/s
Enumerable#reverse.detect:  2649731.9 i/s - 1.93x  (± 0.00) slower

$ ruby -v code/enumerable/map-flatten-vs-flat_map.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
Array#map.flatten(1)    19.228k i/100ms
   Array#map.flatten    20.489k i/100ms
      Array#flat_map    54.160k i/100ms
Calculating -------------------------------------
Array#map.flatten(1)    221.737k (± 3.1%) i/s -      1.115M in   5.034573s
   Array#map.flatten    221.789k (± 4.0%) i/s -      1.127M in   5.089857s
      Array#flat_map    572.127k (± 2.8%) i/s -      2.870M in   5.021272s

Comparison:
      Array#flat_map:   572127.2 i/s
   Array#map.flatten:   221788.9 i/s - 2.58x  (± 0.00) slower
Array#map.flatten(1):   221737.5 i/s - 2.58x  (± 0.00) slower

$ ruby -v code/enumerable/each-push-vs-map.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
   Array#each + push   290.941k i/100ms
           Array#map     1.503M i/100ms
Calculating -------------------------------------
   Array#each + push      3.307M (± 3.2%) i/s -     16.584M in   5.019505s
           Array#map     14.974M (± 4.3%) i/s -     75.165M in   5.030240s

Comparison:
           Array#map: 14973582.9 i/s
   Array#each + push:  3307322.3 i/s - 4.53x  (± 0.00) slower

$ ruby -v code/time/iso8601-vs-parse.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        Time.iso8601    22.182k i/100ms
          Time.parse   205.000  i/100ms
Calculating -------------------------------------
        Time.iso8601    395.250k (±18.5%) i/s -      1.863M in   5.038406s
          Time.parse      9.775k (±23.3%) i/s -     38.540k in   5.012134s

Comparison:
        Time.iso8601:   395250.2 i/s
          Time.parse:     9775.4 i/s - 40.43x  (± 0.00) slower

$ ruby -v code/proc-and-block/proc-call-vs-yield.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          block.call   198.215M i/100ms
       block + yield   202.605M i/100ms
        unused block   211.377M i/100ms
               yield   214.492M i/100ms
Calculating -------------------------------------
          block.call      2.119B (± 3.4%) i/s -     10.704B in   5.056737s
       block + yield      2.118B (± 2.7%) i/s -     10.738B in   5.072990s
        unused block      2.118B (± 3.0%) i/s -     10.780B in   5.095396s
               yield      2.108B (± 2.7%) i/s -     10.725B in   5.092645s

Comparison:
          block.call: 2119313508.4 i/s
       block + yield: 2118280022.8 i/s - same-ish: difference falls within error
        unused block: 2117620032.3 i/s - same-ish: difference falls within error
               yield: 2107519096.9 i/s - same-ish: difference falls within error

$ ruby -v code/proc-and-block/block-vs-to_proc.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
               Block    50.819k i/100ms
      Symbol#to_proc    56.348k i/100ms
Calculating -------------------------------------
               Block    573.078k (± 4.3%) i/s -      2.897M in   5.064722s
      Symbol#to_proc    564.349k (± 3.9%) i/s -      2.874M in   5.100597s

Comparison:
               Block:   573077.9 i/s
      Symbol#to_proc:   564349.2 i/s - same-ish: difference falls within error

$ ruby -v code/string/sub!-vs-gsub!-vs-[]=.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#['string']=    20.483M i/100ms
 String#sub!'string'    42.626k i/100ms
String#gsub!'string'   127.201k i/100ms
  String#[/regexp/]=     3.099M i/100ms
 String#sub!/regexp/     1.332M i/100ms
String#gsub!/regexp/   570.182k i/100ms
Calculating -------------------------------------
  String#['string']=    221.320M (± 3.8%) i/s -      1.106B in   5.005456s
 String#sub!'string'    438.216k (± 3.1%) i/s -      2.217M in   5.062935s
String#gsub!'string'      1.206M (±10.2%) i/s -      5.978M in   5.047787s
  String#[/regexp/]=     30.016M (± 4.2%) i/s -    151.875M in   5.069432s
 String#sub!/regexp/     12.939M (± 3.4%) i/s -     65.269M in   5.050437s
String#gsub!/regexp/      7.066M (± 3.5%) i/s -     35.351M in   5.009731s

Comparison:
  String#['string']=: 221320426.2 i/s
  String#[/regexp/]=: 30016022.3 i/s - 7.37x  (± 0.00) slower
 String#sub!/regexp/: 12939209.1 i/s - 17.10x  (± 0.00) slower
String#gsub!/regexp/:  7065530.1 i/s - 31.32x  (± 0.00) slower
String#gsub!'string':  1205541.2 i/s - 183.59x  (± 0.00) slower
 String#sub!'string':   438216.0 i/s - 505.05x  (± 0.00) slower

$ ruby -v code/string/unpack1-vs-unpack[0].rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      String#unpack1     1.896M i/100ms
    String#unpack[0]     2.077M i/100ms
Calculating -------------------------------------
      String#unpack1     20.642M (± 4.1%) i/s -    104.253M in   5.059977s
    String#unpack[0]     21.120M (± 2.3%) i/s -    105.931M in   5.018447s

Comparison:
    String#unpack[0]: 21120055.1 i/s
      String#unpack1: 20642104.0 i/s - same-ish: difference falls within error

$ ruby -v code/string/dup-vs-unary-plus.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#+@   198.705M i/100ms
          String#dup   212.374M i/100ms
Calculating -------------------------------------
           String#+@      2.124B (± 2.7%) i/s -     10.730B in   5.056341s
          String#dup      2.060B (± 3.6%) i/s -     10.406B in   5.058564s

Comparison:
           String#+@: 2123689800.5 i/s
          String#dup: 2059916487.8 i/s - same-ish: difference falls within error

$ ruby -v code/string/concatenation.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
            String#+   208.878M i/100ms
       String#concat   343.062M i/100ms
       String#append   213.876M i/100ms
         "foo" "bar"   214.057M i/100ms
  "#{'foo'}#{'bar'}"   211.501M i/100ms
Calculating -------------------------------------
            String#+      2.130B (± 2.1%) i/s -     10.653B in   5.002642s
       String#concat      3.386B (± 2.7%) i/s -     17.153B in   5.069131s
       String#append      2.102B (± 4.0%) i/s -     10.694B in   5.096638s
         "foo" "bar"      2.101B (± 4.4%) i/s -     10.489B in   5.001656s
  "#{'foo'}#{'bar'}"      2.108B (± 3.8%) i/s -     10.575B in   5.024132s

Comparison:
       String#concat: 3386382934.2 i/s
            String#+: 2130382248.5 i/s - 1.59x  (± 0.00) slower
  "#{'foo'}#{'bar'}": 2108175440.4 i/s - 1.61x  (± 0.00) slower
       String#append: 2101785543.2 i/s - 1.61x  (± 0.00) slower
         "foo" "bar": 2101461114.0 i/s - 1.61x  (± 0.00) slower

$ ruby -v code/string/start-string-checking-match-vs-start_with.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~     2.888M i/100ms
       String#match?     4.896M i/100ms
  String#start_with?     2.832M i/100ms
Calculating -------------------------------------
           String#=~     29.763M (± 5.4%) i/s -    150.199M in   5.063060s
       String#match?     48.252M (± 3.0%) i/s -    244.805M in   5.078359s
  String#start_with?     27.684M (± 4.1%) i/s -    138.761M in   5.021134s

Comparison:
       String#match?: 48252159.5 i/s
           String#=~: 29763186.0 i/s - 1.62x  (± 0.00) slower
  String#start_with?: 27683749.1 i/s - 1.74x  (± 0.00) slower

$ ruby -v code/string/sub-vs-delete_prefix.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#delete_prefix     3.313M i/100ms
          String#sub   225.604k i/100ms
Calculating -------------------------------------
String#delete_prefix     34.498M (± 4.8%) i/s -    172.281M in   5.006938s
          String#sub     14.467M (± 9.7%) i/s -     71.742M in   5.008398s

Comparison:
String#delete_prefix: 34497903.1 i/s
          String#sub: 14467057.0 i/s - 2.38x  (± 0.00) slower

$ ruby -v code/string/casecmp-vs-downcase-==.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
String#downcase + ==     2.080M i/100ms
      String#casecmp     4.720M i/100ms
Calculating -------------------------------------
String#downcase + ==     25.090M (± 3.8%) i/s -    126.886M in   5.064913s
      String#casecmp     47.588M (± 2.7%) i/s -    240.723M in   5.062479s

Comparison:
      String#casecmp: 47587774.9 i/s
String#downcase + ==: 25089746.2 i/s - 1.90x  (± 0.00) slower

$ ruby -v code/string/mutable_vs_immutable_strings.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
      Without Freeze   204.181M i/100ms
         With Freeze   213.713M i/100ms
Calculating -------------------------------------
      Without Freeze      2.123B (± 3.2%) i/s -     10.617B in   5.007281s
         With Freeze      2.128B (± 2.6%) i/s -     10.686B in   5.025810s

Comparison:
         With Freeze: 2127610579.7 i/s
      Without Freeze: 2122729313.5 i/s - same-ish: difference falls within error

$ ruby -v code/string/gsub-vs-tr.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    80.123k i/100ms
           String#tr   259.348k i/100ms
Calculating -------------------------------------
         String#gsub      3.534M (± 7.7%) i/s -     17.627M in   5.019161s
           String#tr      2.756M (± 5.8%) i/s -     13.745M in   5.006436s

Comparison:
         String#gsub:  3533574.2 i/s
           String#tr:  2755638.1 i/s - 1.28x  (± 0.00) slower

$ ruby -v code/string/sub-vs-chomp-vs-delete_suffix.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
          String#sub   198.998k i/100ms
        String#chomp     7.731M i/100ms
String#delete_suffix     7.665M i/100ms
Calculating -------------------------------------
          String#sub     13.250M (± 9.5%) i/s -     65.669M in   5.004709s
        String#chomp     77.948M (± 2.0%) i/s -    394.272M in   5.060182s
String#delete_suffix     80.884M (± 2.8%) i/s -    406.256M in   5.026785s

Comparison:
String#delete_suffix: 80884288.2 i/s
        String#chomp: 77947790.7 i/s - same-ish: difference falls within error
          String#sub: 13249878.6 i/s - 6.10x  (± 0.00) slower

$ ruby -v code/string/remove-extra-spaces-or-other-chars.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
 String#gsub/regex+/     5.245k i/100ms
      String#squeeze   100.270k i/100ms
Calculating -------------------------------------
 String#gsub/regex+/    141.830k (± 5.2%) i/s -    708.075k in   5.006844s
      String#squeeze      1.007M (± 4.1%) i/s -      5.114M in   5.086051s

Comparison:
      String#squeeze:  1007285.6 i/s
 String#gsub/regex+/:   141830.0 i/s - 7.10x  (± 0.00) slower

$ ruby -v code/string/===-vs-=~-vs-match.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
       String#match?     8.990M i/100ms
           String#=~     8.868M i/100ms
          Regexp#===     8.412M i/100ms
        String#match     7.695M i/100ms
Calculating -------------------------------------
       String#match?     92.033M (± 3.9%) i/s -    467.455M in   5.087638s
           String#=~     85.823M (± 3.8%) i/s -    434.529M in   5.070739s
          Regexp#===     85.938M (± 2.1%) i/s -    437.417M in   5.092125s
        String#match     76.844M (± 3.2%) i/s -    384.746M in   5.012338s

Comparison:
       String#match?: 92032736.3 i/s
          Regexp#===: 85937733.9 i/s - 1.07x  (± 0.00) slower
           String#=~: 85822677.2 i/s - same-ish: difference falls within error
        String#match: 76843647.0 i/s - 1.20x  (± 0.00) slower

$ ruby -v code/string/start_with-vs-substring-==.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
  String#start_with?   261.226k i/100ms
    String#[0, n] ==   158.638k i/100ms
   String#[RANGE] ==   181.650k i/100ms
   String#[0...n] ==   137.238k i/100ms
Calculating -------------------------------------
  String#start_with?      4.716M (± 4.2%) i/s -     23.772M in   5.049932s
    String#[0, n] ==      3.597M (± 4.9%) i/s -     18.085M in   5.039606s
   String#[RANGE] ==      3.804M (± 4.8%) i/s -     19.073M in   5.026822s
   String#[0...n] ==      2.835M (± 5.1%) i/s -     14.136M in   5.001452s

Comparison:
  String#start_with?:  4715868.6 i/s
   String#[RANGE] ==:  3803892.4 i/s - 1.24x  (± 0.00) slower
    String#[0, n] ==:  3597270.2 i/s - 1.31x  (± 0.00) slower
   String#[0...n] ==:  2835076.7 i/s - 1.66x  (± 0.00) slower

$ ruby -v code/string/gsub-vs-sub.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
         String#gsub    76.816k i/100ms
          String#sub    45.953k i/100ms
String#dup["string"]=
                        16.701M i/100ms
Calculating -------------------------------------
         String#gsub      1.190M (± 5.0%) i/s -      5.992M in   5.050719s
          String#sub    457.294k (± 3.5%) i/s -      2.298M in   5.030746s
String#dup["string"]=
                        164.315M (± 3.2%) i/s -    835.027M in   5.087231s

Comparison:
String#dup["string"]=: 164315344.0 i/s
         String#gsub:  1189618.5 i/s - 138.12x  (± 0.00) slower
          String#sub:   457294.4 i/s - 359.32x  (± 0.00) slower

$ ruby -v code/string/end-string-checking-match-vs-end_with.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
           String#=~     1.636M i/100ms
       String#match?     2.231M i/100ms
    String#end_with?    21.672M i/100ms
Calculating -------------------------------------
           String#=~     16.509M (± 3.1%) i/s -     83.428M in   5.058491s
       String#match?     24.129M (± 2.9%) i/s -    122.683M in   5.088854s
    String#end_with?    223.659M (± 2.5%) i/s -      1.127B in   5.042115s

Comparison:
    String#end_with?: 223659001.8 i/s
       String#match?: 24128941.6 i/s - 9.27x  (± 0.00) slower
           String#=~: 16509499.1 i/s - 13.55x  (± 0.00) slower

$ ruby -v code/range/cover-vs-include.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
        range#cover?    30.877k i/100ms
      range#include?   181.000  i/100ms
       range#member?   270.000  i/100ms
       plain compare    32.154k i/100ms
Calculating -------------------------------------
        range#cover?    374.504k (±56.2%) i/s -      1.359M in   5.033366s
      range#include?      5.135k (±65.2%) i/s -     16.290k in   5.036044s
       range#member?      2.770k (±29.7%) i/s -     13.230k in   5.949872s
       plain compare    209.760k (±21.2%) i/s -      1.029M in   5.090929s

Comparison:
        range#cover?:   374503.8 i/s
       plain compare:   209759.9 i/s - same-ish: difference falls within error
      range#include?:     5134.5 i/s - 72.94x  (± 0.00) slower
       range#member?:     2770.0 i/s - 135.20x  (± 0.00) slower

$ ruby -v code/method/call-vs-send-vs-method_missing.rb
truffleruby 21.3.0-dev-d772ae7b, like ruby 2.7.3, GraalVM CE Native [x86_64-darwin]
Warming up --------------------------------------
                call   207.684M i/100ms
                send   189.186M i/100ms
      method_missing   216.122M i/100ms
Calculating -------------------------------------
                call      2.099B (± 3.1%) i/s -     10.592B in   5.050963s
                send      2.119B (± 3.3%) i/s -     10.594B in   5.005398s
      method_missing      2.127B (± 2.3%) i/s -     10.806B in   5.082870s

Comparison:
      method_missing: 2127154272.5 i/s
                send: 2119099951.0 i/s - same-ish: difference falls within error
                call: 2099160015.0 i/s - same-ish: difference falls within error



```



## License

![CC-BY-SA](CC-BY-SA.png)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Code License

### CC0 1.0 Universal

To the extent possible under law, @JuanitoFatas has waived all copyright and related or neighboring rights to "fast-ruby".

This work belongs to the community.
