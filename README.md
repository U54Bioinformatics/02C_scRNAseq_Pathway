## run ssGSEA using Betsy  
betsy_run.py --network_png ssgsea.pdf --num_cores 23 \\  
--input SignalFile --input_file counts.txt \\  
--dattr SignalFile.preprocess=counts \\  
--output ssGSEAResults --output_file dir_to_the_output \\  
***--mattr geneset_file=.gmt \\***   
***--mattr geneset_file2=.gmt \\***  
--mattr gsva_min_geneset_size=10 \\  
--mattr gsva_max_geneset_size=1000 \\  
--run

> *An alternative\:*  
> ***--mattr geneset_database=hallmarks***  
> ***--mattr geneset_database2=curated***  

> *ZINB-WaVE Normalization*  
> ***--dattr ssGSEAResults.zinbwave_norm=yes***   
> (Optional -- if you want to change the covariates)  
> ***--mattr sample_covariate=genes***  
> ***--mattr gene_covariate=gc+log_transcriptlen***  


## Statistical test on ssGSEA scores among groups  
betsy_run.py --network_png de02.pdf --num_cores 20 --receipt receipt.txt \\  
--input SignalFile --input_file scores.txt \\  
--dattr SignalFile.logged=not_applicable \\  
--input SimpleClassFile --input_file simple_class.txt \\    
--output DiffExpAnalysis --output_file dir_to_the_output \\  
--dattr DiffExpAnalysis.de_algorithm=ttest \\  
***--dattr DiffExpAnalysis.de_comparison=all_vs_all \\***  
--mattr p_cutoff=0.05 \\  
--mattr plot_max_genes_per_group=11

> **Alternatives\:**  
> ***--dattr DiffExpAnalysis.de_comparison=one_vs_others***  
>
> **Notes\:**  
> simple_class.txt: The format is two columns and tab-deliminated.  The headers should be 'Sample' and 'Class'.  The 'Sample' column should be identical to the column names of the 'scores.txt' file and the 'Class' column could be annotation or other grouping factors. 

## References and documentation 
References: 
GSVA [Hänzelmann et al. BMC Bioinformatics (2013)](https://doi.org/10.1186/1471-2105-14-7)
ZINB-WaVE [Risso et al. Nature Communications (2018)](https://doi.org/10.1038/s41467-017-02554-5)
