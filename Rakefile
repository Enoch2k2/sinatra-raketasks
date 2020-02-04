task :console do
  Pry.start
end

task :drop_db do
  puts "Dropping Database"
  system('db/development.sqlite')
  puts "Dropped Database"
end

task :start_server do
  puts "Starting Server"
  system("shotgun")
end

task :migrate_all do
   puts "Migrating Development And Testing Database"
   system("rake db:migrate && rake db:migrate SINATRA_ENV=test")
end

task :reset_all do
  Rake::Tasks[:drop_db].execute
  Rake::Tasks[:migrate_all].execute
  puts "Seeding Database..."
  system("rake db:seed")
  puts "Database Seeded, now starting server"
  Rake::Tasks[:start_server].execute
end
