# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require_relative "config/application"

task default: %i[sanitize clean]

task :interpret do
  puts "Interpreting the code"
end

desc "Cleaning the code"
task :clean do
  puts "Cleaning the code up"
end

desc "Sanitizing the code"
task :sanitize do
  puts "Sanitize the code before use"
end

desc "Compile Code"
task compile: %i[clean sanitize interpret]  do
  puts "Compiling the code."
end

Rails.application.load_tasks
