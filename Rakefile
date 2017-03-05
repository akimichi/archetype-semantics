# -*- coding: utf-8 -*-
# require 'rubygems'
require 'rake'
 
TEX_FILES = FileList['manuscript.tex']
DVI_FILES = TEX_FILES.ext('dvi')
PDF_FILES = TEX_FILES.ext('pdf')
AUX_FILES = TEX_FILES.ext('aux')
 
# task :default => :supplement
task :default => PDF_FILES

rule ".tex" => ".aux" do |t|
  sh "rm #{t.source}"
end

rule ".dvi" => ".tex" do |t|
 2.times  do
   sh "platex #{t.source}"
 end
 p t.source
end

rule '.pdf' => '.dvi' do |t|
  sh "dvipdfmx #{t.source}"
end


namespace "check" do
  SOURCE = 'paper'
  TEX_FILE = "#{SOURCE}.tex"
  DVI_FILE = TEX_FILE.ext('dvi')
  PDF_FILE = TEX_FILE.ext('pdf')
  # http://matt.might.net/articles/shell-scripts-for-passive-voice-weasel-words-duplicates/
  task :all => [:weasel, :passive, :duplicate]

  task :weasel do |t|
    p "WEASEL WORDS: "
    sh "sh ../../bin/weasel_check.sh #{TEX_FILE}"
  end
  task :passive do |t|
    p "PASSIVE VOICE: "
    sh "sh ../../bin/passive_check.sh #{TEX_FILE}"
  end
  task :duplicate do |t|
    p "DUPLICATES: "
    sh "perl ../../bin/duplicate_check.pl #{TEX_FILE}"
  end
  task :style do |t|
    p "style-check: "
    sh "sh ../../bin/style-check/style-check.rb #{TEX_FILE}"
  end
end

task :supplement do |t|
  SOURCE = 'supplement'
  TEX_FILE = "#{SOURCE}.tex"
  DVI_FILE = TEX_FILE.ext('dvi')
  PDF_FILE = TEX_FILE.ext('pdf')
  2.times  do
    sh "platex #{TEX_FILE}"
  end
  sh "makeglossaries #{SOURCE}"
  sh "dvipdfmx #{DVI_FILE}"
end
