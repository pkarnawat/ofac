require 'rubygems'
require 'rake'
require 'yaml'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "ofac"
    gem.summary = %Q{Attempts to find a hit on the Office of Foreign Assets Control's Specially Designated Nationals list.}
    gem.description = %Q{Attempts to find a hit on the Office of Foreign Assets Control's Specially Designated Nationals list.}
    gem.email = "kevintyll@gmail.com"
    gem.homepage = "http://github.com/kevintyll/ofac"
    gem.authors = ["Kevin Tyll"]
    gem.post_install_message = File.readlines("PostInstall.txt").join("")
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end

  Jeweler::GemcutterTasks.new

rescue LoadError
  puts "Jeweler not available. Install it with: sudo gem install technicalpickles-jeweler -s http://gems.github.com"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/*_test.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/*_test.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end


task :default => :test

require 'rdoc/task'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION.yml')
    config = YAML.load(File.read('VERSION.yml'))
    version = "#{config[:major]}.#{config[:minor]}.#{config[:patch]}"
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "ofac #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

