require 'rake/clean'

source_files = "resume"
org = "#{source_files}.org"
tex = "#{source_files}.tex"
pdf = "#{source_files}.pdf"

CLEAN.include(tex, pdf, '*~')

pandoc_tex_header = "pandoc/header.tex"

file tex => [org, pandoc_tex_header] do
  sh "pandoc #{org} --pdf-engine=xelatex" +
     " -H #{pandoc_tex_header} -o #{tex}"
end

file pdf => [org, pandoc_tex_header] do
  sh "pandoc #{org} --pdf-engine=xelatex" +
     " -H #{pandoc_tex_header} -o #{pdf}"
end

task :default => [pdf]
desc 'Build pdf files from tex file'
task pdf: source_files.ext('.pdf')
desc 'Build tex files from org file'
task tex: source_files.ext('.tex')
