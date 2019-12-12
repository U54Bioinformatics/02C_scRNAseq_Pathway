## run ssGSEA using Betsy  
betsy_run.py --network_png ssgsea.pdf --num_cores 23 \\  
--input SignalFile --input_file counts.txt \\  
--dattr SignalFile.preprocess=count \\  
--output ssGSEAResults --output_file out-ssgsea \\  
***--mattr geneset_file=.gmt \\***   
***--mattr geneset_file2=.gmt \\***  
--mattr gsva_min_geneset_size=10 \\  
--mattr gsva_max_geneset_size=1000 \\  
--run

> *An alternative\:*  
> ***--mattr geneset_database=hallmarks***  
> ***--mattr geneset_database2=curated***  

## Statistical test on ssGSEA scores among groups  
betsy_run.py --network_png de02.pdf --num_cores 20 --receipt receipt.txt \\  
--input SignalFile --input_file scores.txt \\  
--dattr SignalFile.logged=not_applicable \\  
--input SimpleClassFile --input_file simple_class.txt \\ \# two columns in this file: 'Sample' and 'Class'; 'Sample' should be identical to the column names of the "scores.txt", 'Class' could be annotation or grouping factors.   
--output DiffExpAnalysis --output_file out-directory_to_output \\  
--dattr DiffExpAnalysis.de_algorithm=ttest \\  
--dattr DiffExpAnalysis.de_comparison=all_vs_all \\  
--mattr p_cutoff=0.05 \\  
--mattr plot_max_genes_per_group=11

> *Alternative\:*  
> ***--dattr DiffExpAnalysis.de_comparison=one_vs_others***  
> ***--mattr geneset_database2=curated***  
