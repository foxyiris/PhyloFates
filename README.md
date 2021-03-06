# PhyloFates
PhyloFates is an estimation algorithm for evolution of protein targeting signal.  
Basic idea came from [CLIME](http://gene-clime.org/) using phylogenetic profiling for gene gain/loss, and we expanded this to targeting signal.
One motivation of this algorithm is automatic detection of widely conserved targeting signal from numerous gene clusters.  
Concept of homology is hard to be applied in this task, since targeting signal is usually not conserved in a primary structure level. 
However, targeting signal of orthologs is basically conserved, inferring conservation not in primary sequence but in feature space.  
Assuming there is no re-entrant into feature space of targeting signal from outside, we can simply model evolution of targeting signal with some prediction algotirhms.  
At present, we applied PhyloFates for estimation of presequence evolution with [MitoFates](http://mitf.cbrc.jp/MitoFates) program.  
PhyloFates is not restricted to MitoFates, and an arbitrary discrete feature is applicable.  
When you are interested in another application with a different system, contact me freely. Let's collaborate.
## Installation
This project is coded in ruby (partly in C), so you don't need to compile.
Download and enjoy!  
Check Gemfile for dependency.

Dependency:  
1. bioruby  
2. GSL (required ruby binding)  
3. RubyInline  
4. parallel  
5. prawn (optional)

## Setting
Before starting you need to change some default values.  
In main.rb:  
```
	model_file_path=  
	total_step=  
	burn_in=  
```
In addition, you may need to change output dir of log file.  
In class/infer_hist.rb:  
```
	#in the initialize constructor
	@log_file=   
```

## Usage

ruby main.rb tree_file(newick format) phylogenetic_profile(CLIME format)  
e.g. ruby main.rb tree.nwk ./toydata/Tim50_revised.csv  

When you need a graphical representation, draw_profile script is useful.  
model_dir is a directory for output of main.rb.  
ruby draw_profile.rb tree_file(newick format) phylogenetic_profile(CLIME format) model_dir output_dir  
e.g. ruby main.rb tree.nwk ./toydata/Tim50_revised.csv ./models/ ./pdfs/

## Contributing
1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## Credits
Yoshinori Fukasawa
