#!/usr/bin/env rake

desc "Update assets"
task :update do
  system("rm -rf bootstrap-datepicker-src")
  system("git clone git://github.com/eternicode/bootstrap-datepicker.git bootstrap-datepicker-src")
  system("cp bootstrap-datepicker-src/css/datepicker.css vendor/assets/stylesheets/bootstrap-datepicker.css")
  system("cp bootstrap-datepicker-src/js/bootstrap-datepicker.js vendor/assets/javascripts/bootstrap-datepicker/core.js")
  system("cp -R bootstrap-datepicker-src/js/locales/ vendor/assets/javascripts/bootstrap-datepicker/locales/")
  fixes
  system("git status")  
end

def fixes
  puts "hello"
  core_file = File.read("vendor/assets/javascripts/bootstrap-datepicker/locales/bootstrap-datepicker.ms.js")
  string = 'monthsShort: ["Jan", "Feb", "Mar", "Apr", "Mei", "Jun", "Jul", "Ogo", "Sep", "Okt", "Nov", "Dis"]'
  modified_file = core_file.gsub(string, string + ',')
  File.open("vendor/assets/javascripts/bootstrap-datepicker/locales/bootstrap-datepicker.ms.js", "w") { |file| file.puts modified_file }  
end

desc "Build and publish de gem"
task "build" do    
  system("gem build bootstrap-datepicker-rails.gemspec")
end

desc "Build and publish de gem"
task "publish" do    
  require File.expand_path('../lib/bootstrap-datepicker-rails/version', __FILE__)
  system("gem push bootstrap-datepicker-rails-#{BootstrapDatepickerRails::Rails::VERSION}.gem")  
  system("git push")
end