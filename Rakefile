
desc "start pry session"
task :console do
  Pry.start
end

desc "drop both development and testing database"
task :drop_db do
  puts "Dropping Database"
  system('rm db/development.sqlite')
  system('rm db/test.sqlite')
  puts "Dropped Database"
end

desc "Start shotgun server"
task :start_server do
  puts "Starting Server"
  system("shotgun")
end

desc "migrate both development and testing database"
task :migrate_all do
   puts "Migrating Development And Testing Database"
   system("rake db:migrate && rake db:migrate SINATRA_ENV=test")
end

desc "drop db, remigrate db, seed, start server"
task :reset_all do
  Rake::Task['drop_db'].invoke
  Rake::Task['migrate_all'].invoke
  puts "Seeding Database..."
  system("rake db:seed")
  puts "Database Seeded, now starting server"
  Rake::Task['start_server'].invoke
end
