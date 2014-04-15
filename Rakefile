require 'rake/clean'

resume = "xiaohanyu_resume"
org_resume = "#{resume}.org"
tex_resume = "#{resume}.tex"
pdf_resume = "#{resume}.pdf"
html_resume = "#{resume}.html"

CLEAN.include(tex_resume, pdf_resume, html_resume, '*~')

pandoc_tex_header = "header.tex"


file tex_resume => [org_resume, pandoc_tex_header] do
  sh "pandoc -s #{org_resume} --latex-engine=xelatex" +
     " -H #{pandoc_tex_header} -o #{tex_resume}"
end

file pdf_resume => [org_resume, pandoc_tex_header] do
  sh "pandoc -s #{org_resume} --latex-engine=xelatex" +
     " -H #{pandoc_tex_header} -o #{pdf_resume}"
end

file html_resume => [org_resume] do
  sh "pandoc -s #{org_resume} -o #{html_resume}"
end

task :default => [pdf_resume, html_resume]
