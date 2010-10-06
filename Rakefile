require 'rake/gempackagetask'
require 'rubygems/specification'
require 'bundler'

GEM         = "cinderella"
GEM_VERSION = "0.2.5.1"
AUTHOR      = "Headshift"
EMAIL       = "no-reply@headshift.com"
HOMEPAGE    = "http://github.com/headshift/cinderella"
SUMMARY     = "Set-up Mac development environment - This is a fork of http://github.com/atmos/cinderella"

spec = Gem::Specification.new do |s|
  s.name             = GEM
  s.version          = GEM_VERSION
  s.platform         = Gem::Platform::RUBY
  s.has_rdoc         = true
  s.extra_rdoc_files = ["LICENSE"]
  s.summary          = SUMMARY
  s.description      = s.summary
  s.author           = AUTHOR
  s.email            = EMAIL
  s.homepage         = HOMEPAGE

  bundle = Bundler::Definition.build('Gemfile', 'Gemfile.lock', { })
  bundle.dependencies.each do |dep|
    next unless dep.groups.include?(:runtime)
    s.add_dependency(dep.name, dep.version_requirements.to_s)
  end

  s.bindir       = "bin"
  s.executables  = %w( cinderella )
  s.require_path = 'lib'
  s.files        = %w(LICENSE README.md Rakefile) + Dir.glob("{lib}/**/*")
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end
