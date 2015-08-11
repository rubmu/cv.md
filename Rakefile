desc 'Build the HTML code for the CV, using the template and the md source'
task :build do
  sh 'cat header.html > cv.html'
  sh 'bundle exec redcarpet --smarty cv.md >> cv.html'
  sh 'cat footer.html >> cv.html'
end
