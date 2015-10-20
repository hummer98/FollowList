project_name = "FollowList"

desc "Initial setup"
task :setup do
  sh "brew install rbenv ruby-build rbenv-gem-rehash rbenv-binstubs carthage"
  sh "echo 'if ! [[ $(which rbenv) =~ \"rbenv\" ]]; then eval \"$(rbenv init -)\" && source ~/.bash_profile; fi' >> ~/.bash_profile"
  sh "rbenv install `cat .ruby-version`" do |is_success, status|
    p "WARN: ignore error." unless is_success
  end
  sh "gem install bundler"
  Rake::Task["update"].invoke
end

desc "Open workspace"
task :open do
  sh "open #{project_name}.xcworkspace"
end

desc "library update"
task :update do
  sh "bundle install"
  sh "pod install"
  sh "carthage checkout"
  sh "carthage build --platform iOS"
end

desc "run synx"
task :synx do |t|
  sh "synx #{project_name}.xcodeproj/"
end