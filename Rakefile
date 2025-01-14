# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.
# Source:
# https://www.writesoftwarewell.com/a-brief-introduction-to-rake/

require_relative "config/application"

# Providing Defaults
# Use the default task to specify all tasks to run when
# we run the rake command, without any arguments
task default: %i[sanitize clean]

# Dependent Task used by Compile Code
task :interpret do
  puts "Interpreting the code"
end

# Dependent Task used by Compile Code
desc "Cleaning the code"
task :clean do
  puts "Cleaning the code up"
end

# Dependent Task used by Compile Code
desc "Sanitizing the code"
task :sanitize do
  puts "Sanitize the code before use"
end

# rake which uses the dependent tasks
desc "Compile Code"
task compile: %i[clean sanitize interpret]  do
  puts "Compiling the code."
end

# Scope
# We can scope tasks with similar names under different namespaces
task :backup do
  puts "Database backup"
end

namespace :file do
  task :backup do
    puts "File backup"
  end
end

# Access Environment Variables
# Rake also allows to pass the environment variable for the particular
# command. It's only valid for that specific command, though
# Example: export STATE=paused
task :show_state do
  puts "State = #{ENV["STATE"]}"
end

# Whats possible with rake?
# Since it's ruby itself we can do anything that is possible in ruby itself
# There's No limit
# Example code
task :sum do
  result = 0
  (1..10).each do |n|
    result += n
  end
  puts result
end

# As mentioned in the blog rake is perfect for file manipulation
# It includes FileUtils & Standard library.
# So we can use all standard file manipulation commands

desc "Taking a backup of the Rakefile"
task :backup do
  mkdir_p "data/backup"
  cp "Rakefile", "data/backup/Rakefile"
end

# We can also run shells Command (Which is gonna be very useful)
# Example: This is especially handy when we want to run git
# add , commit, push commands.

desc "git add, commit, and push"
task :track do
  sh "git add ."
  sh "git commit -m '#{ENV['m']}' "
  sh "git push origin main"
end

Rails.application.load_tasks
