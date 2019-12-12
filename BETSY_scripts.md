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
--input SimpleClassFile --input_file simple_class.txt \\    
--output DiffExpAnalysis --output_file out-directory_to_output \\  
--dattr DiffExpAnalysis.de_algorithm=ttest \\  
--dattr DiffExpAnalysis.de_comparison=all_vs_all \\  
--mattr p_cutoff=0.05 \\  
--mattr plot_max_genes_per_group=11

> **Alternatives\:**  
> ***--dattr DiffExpAnalysis.de_comparison=one_vs_others***  
>
> **Notes\:**  
> simple_class.txt: The format is two columns and tab-deliminated.  The headers should be 'Sample' and 'Class'.  The 'Sample' column should be identical to the column names of the 'scores.txt' file and the 'Class' column could be annotation or other grouping factors. 