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
end
