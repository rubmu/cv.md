namespace :build do
  desc 'Build the HTML code for the CV, using the template and the md source'
  task :html do
    sh 'cat header.html > cv.html'
    sh 'bundle exec redcarpet --smarty cv.md >> cv.html'
    sh 'cat footer.html >> cv.html'
    sh 'mv cv.html cv/'
  end

  desc 'Build the M$ Word version of the CV'
  task :docx do
    sh 'pandoc cv.md -o cv/cv.docx'
  end

  desc 'Build all the CV downloadable versions'
  task :all do
    Rake::Task['build:html'].invoke
    Rake::Task['build:docx'].invoke
  end
end

desc 'Deploy gh-page'
task :deploy do
  sh 'git checkout gh-pages'
  sh 'git rebase origin/master'
  Rake::Task['build:html'].invoke
  sh 'rm index.html' if File.exists? 'index.html'
  sh 'cp cv/cv.html index.html'
  sh 'git add .'
  sh "git commit -m 'Deploy #{Time.now.to_i}'"
  sh 'git push origin gh-pages'
  sh 'git checkout master'
end
