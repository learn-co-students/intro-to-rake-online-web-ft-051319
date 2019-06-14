namespace :greeting do #greeting heading. so when we wanna call rake :hello, it needs to be namespaced -> "rake greeting:hello"
  desc 'outputs hello to the terminal'
  task :hello do
    puts "hello from Rake!"
  end

  desc 'outputs hola to the terminal'
  task :hola do
    puts "hola de Rake!"
  end

end

task :environment do #this rake task is necessary for the one below to work due to task dependency
  require_relative './config/environment'
end

namespace :db do
  desc 'migrate changes to your database'
  task :migrate => :environment do
    Student.create_table #task dependency: our Student.create_table code would require access to the config/environment.rb file
  end

  desc 'seed the database with some dummy data' #responsible for "seeding" our database with some dummy data. This comes from the seeds.rb file in db
  task :seed do
    require_relative './db/seeds.rb'
  end

end


desc 'drop into the Pry console'
task :console => :environment do #this means the task is dependent on the environment task so that Student class and database connection load first
  Pry.start
end
