require 'rubygems'
require 'less'
require 'rake'
 
SOURCE = "."

CONFIG = {
  'less'   => File.join( SOURCE, "less" ),
  'css'    => File.join( SOURCE, "css" ),
  'input'  => "main.less",
  'output' => "main.css"
}

desc "Compile Less"
task :lessc do
  less   = CONFIG['less']
 
  input  = File.join( less, CONFIG['input'] )
  output = File.join( CONFIG['css'], CONFIG['output'] )
 
  source = File.open( input, "r" ).read
 
  parser = Less::Parser.new( :paths => [less] )
  tree = parser.parse( source )
 
  File.open( output, "w+" ) do |f|
    f.puts tree.to_css( :compress => true )
  end
end

task :default do 
	Rake::Task["lessc"].invoke
end