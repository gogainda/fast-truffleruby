desc "run benchmark in current ruby"
task :run_benchmark do
  Dir["code/general/*.rb"].each do |benchmark|
    puts "$ ruby -v #{benchmark}"
    system("BENCHMARK_IPS_FORCE_WARMUP=5 ruby", "-v", "-W0", benchmark)
  end

  Dir["code/*/*.rb"].reject { |path| path =~ /^code\/general/ }.each do |benchmark|
    puts "$ ruby -v #{benchmark}"
    system("BENCHMARK_IPS_FORCE_WARMUP=5 ruby", "-v", "-W0", benchmark)
  end
end

task default: :run_benchmark
