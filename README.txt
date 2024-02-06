Misperceived Social Norms: Women Working Outside the Home in Saudi Arabia

Leonardo Bursztyn, Alessandra L. González, David Yanagizawa-Drott

Data Repository ("openicpsr-119404")

Data Availability Statements
----------------------------

1. The Arab Barometer Wave II (2010-2011) used to support the findings of this study are included in the data/raw_data folder. The raw data can be download from https://www.arabbarometer.org. From the "SURVEY DATA" tab on the webpage, click "AB WAVE II: 2010 - 2011" and download the dataset from "Arab Barometer Wave II: DTA (English)". (Last accessed: May 11 2020) 


Dataset list
------------

|------------------------------------------------------------|--------------------------|----------|------------------------------------------|
| Raw Data File                                              | Source     		| Provided | Notes 				      |
|------------------------------------------------------------|--------------------------|----------|------------------------------------------|                                                
| data/raw_data/01_main_exp_raw1.dta             	     | Main Experiment 		| Yes      | See Notes below                          |
| data/raw_data/01_main_exp_raw2.dta           		     | Main Experiment       	| Yes      | See Notes below  			      |                               
| data/raw_data/02_follow_up_raw1.dta             	     | Follow-up Experiment     | Yes      | First round of follow up                 |
| data/raw_data/02_follow_up_raw2.dta    		     | Follow-up Experiment     | Yes      | Second round of follow up                |
| data/raw_data/03_1st_online_svy_raw.dta    		     | 1st National Survey      | Yes      |                                          |
| data/raw_data/04_2nd_online_svy_raw.dta    		     | 2nd National Survey      | Yes      |                                          |
| data/raw_data/05_recruitment_exp_raw.dta         	     | Recruitment Experiment   | Yes      | 					      |                         
| data/raw_data/06_arab_barometer_raw.dta                    | Arab Barometer Wave II   | Yes      |    				      |
|---------------------------------------------------------------------------------------|----------|------------------------------------------|


|------------------------------------------------------------|--------------------------|----------|------------------------------------------|
| Clean Data File  (as inputs for analysis)                  | Source     		| Provided | Notes 				      |
|------------------------------------------------------------|--------------------------|----------|------------------------------------------|                                                
| data/clean_data/01_main_exp_clean.dta                      | Main Experiment        	| Yes      |     				      |
| data/clean_data/02_follow_up_clean.dta                     | Follow-up Experiment     | Yes      |        				      |
| data/clean_data/03_1st_online_svy_clean.dta                | 1st National Survey      | Yes      |                               	      |
| data/clean_data/04_2nd_online_svy_clean.dta                | 2nd National Survey      | Yes      |   					      |
| data/clean_data/05_recruitment_exp_clean.dta               | Recruitment Experiment   | Yes      |      				      |
| data/clean_data/06_arab_barometer_clean.dta                | Arab Barometer Wave II   | Yes      |  					      |
|---------------------------------------------------------------------------------------|----------|------------------------------------------|


### Notes: 

- 01_main_exp_raw1.dta and 01_main_exp_raw2.dta are both raw data from the main experiment and the observations are identical, except that 01_main_exp_raw2.dta has an additional variable of the last 3 digits of respondents' phone numbers. 01_main_exp_raw1.dta is used to create clean data for the main experiment analysis and 01_main_exp_raw2.dta is used to link responses in the follow-up experiment. Although the two datasets have identical observations, the observations are in different orders and thus which dataset to use matters for the results from the permutation test and bootstrapping in the analysis stage. To perfectly replicate our results, please use the designated dataset for the main experiment and the follow-up. 


Computational requirements
---------------------------

### Software Requirements

- Stata (code was last run with version 15.1): Please note that depending on the version, the p-values from permutation test and wild-bootstrap might be slightly different. Code related to the permute command in the replication package does not work with version 16 or higher. 
  - "boottest"
  - "estout"
  - "mhtexp"
  - "leebounds"
  - "binscatter"
  - All packages above have been pre-installed and stored in the ado folder.


### Description of programs

- The program `code/00_setup.do` will define the path, set up the project folder, and call all required packages stored in the ado folder. This code only needs to be run once at the beginning. 

- The program `code/00_master.do` will run all cleaning and analysis code files.

- Programs in `code/01_cleaning` will transform all raw data referenced above and generate the corresponding clean data for analysis. Output datasets are called appropriate names (e.g. `01_main_exp_clean.dta`) and should be easy to correlate with the analysis codes.

- Programs in `code/02_analysis` will utilize all clean data referenced above and generate all tables or figures in the paper. Each program called from `Master.do' identifies the outputs of the analysis (e.g. `01_analysis_main_exp_figures.do`). Output files are called appropriate names (e.g. `table1.tex` and `appendix_figure1.pdf`) and should be easy to correlate with the manuscript. 

### Memory and Runtime Requirements

The code were last run on a **2-core Intel-based laptop with MacOS version 10.15.4** and took about 40 minutes to complete.


Instructions
------------

1. Open `code/00_setup.do`, modify directory macro to local directory, and run the code to set up. 

2. Open `code/00_master.do` and modify directory macro to local directory. 

3. Run `code/00_master.do` to run all steps in sequence. 


Details 
_______

1. `code/00_setup.do` only needs to be run once at the beginning

2. `code/00_master.do` runs all cleaning and analysis codes in sequence, which should take about 40 minutes. 

3. `code/01_cleaning` 
	
 - These programs were last run at various times in May 2020. 
 - Order does not matter, all programs can be run in parallel if needed. 

4. `code/02_analysis`

 - These programs were last run at various times in May 2020	
 - Random seeds are set for `01_analysis_main_exp_tables.do`, `02_analysis_follow_up_tables.do`, and `05_analysis_recruitment_exp_tables.do'. Thus, for these codes, order is important. If running the code in any order other than the one outlined in the program, your results may slightly differ. 



List of programs and outputs
---------------------------

From raw data to clean data  

|-----------------------------------------------|-----------------------------------------|-----------------------------------------|--------------------|
| Raw Data 					| Program 				  | Clean Data 				    | Note 		 |
|-----------------------------------------------|-----------------------------------------|-----------------------------------------|--------------------|
| raw_data/01_main_exp_raw1.dta	     		| 01_cleaning/01_clean_main_exp.do	  | clean_data/01_main_exp_clean.dta	    |			 |
| raw_data/01_main_exp_raw2.dta     	 	| 01_cleaning/02_clean_follow_up.do	  | clean_data/02_follow_up_clean.dta	    |			 |
| raw_data/02_follow_up_raw1.dta     		| 01_cleaning/02_clean_follow_up.do	  | clean_data/02_follow_up_clean.dta	    |			 |
| raw_data/02_follow_up_raw2.dta     		| 01_cleaning/02_clean_follow_up.do	  | clean_data/02_follow_up_clean.dta	    |			 |
| raw_data/03_1st_online_svy_raw.dta 		| 01_cleaning/03_clean_1st_online_svy.do  | clean_data/03_1st_online_svy_clean.dta  |			 |
| raw_data/04_2nd_online_svy_raw.dta 		| 01_cleaning/04_clean_2nd_online_svy.do  | clean_data/04_2nd_online_svy_clean.dta  |			 |
| raw_data/05_recruitment_exp_raw.dta 		| 01_cleaning/05_clean_recruitment_exp.do | clean_data/05_recruitment_exp_clean.dta | 			 |
| raw_data/06_arab_barometer_raw.dta 		| 01_cleaning/06_clean_arab_barometer.do  | clean_data/06_arab_barometer_clean.dta  |			 |
|-----------------------------------------------|-----------------------------------------|-----------------------------------------|--------------------|


Outputs in the main sections

|-------------------|---------------------------------------------------|-------------|---------------|----------------------------|
| Figure/Table #    | Program                                      	| Line Number | Output file   | Note                       |
|-------------------|---------------------------------------------------|-------------|---------------|----------------------------|
| Figure 1          | n.a. (no data)         		    	   	|             | 	      | Experiment design          |
| Figure 2          | 02_analysis/01_analysis_main_exp_figures.do  	| 22-43       | figure2.pdf   |                            |
| Figure 3          | 02_analysis/01_analysis_main_exp_figures.do  	| 44-77       | figure3.pdf   |                            |
| Figure 4a         | 02_analysis/02_analysis_follow_up_figures.do 	| 19-71       | figure4a.pdf  |                            |
| Figure 4b         | 02_analysis/02_analysis_follow_up_figures.do 	| 72-83       | figure4b.pdf  |                            |
| Figure 4c         | 02_analysis/02_analysis_follow_up_figures.do 	| 84-94       | figure4c.pdf  |                            |
| Figure 4d         | 02_analysis/02_analysis_follow_up_figures.do 	| 95-105      | figure4d.pdf  |                            |
| Figure 5          | 02_analysis/01_analysis_main_exp_figures.do  	| 78-130      | figure5.pdf   |                            |
| Figure 6          | 02_analysis/03_analysis_1st_online_svy_figures.do | 18-54       | figure6.pdf   |          		   |
| Figure 7          | 02_analysis/06_analysis_arab_barometer_figure.do  |             | figure7.pdf   |           		   |
| Figure 8a         | 02_analysis/04_analysis_2nd_online_svy_figures.do | 18-48       | figure8a.pdf  |          		   |
| Figure 8b         | 02_analysis/04_analysis_2nd_online_svy_figures.do | 49-83       | figure8b.pdf  |          		   |
| Figure 9a         | 02_analysis/05_analysis_recruitment_exp_figures.do| 17-55       | figure9a.pdf  | 			   |
| Figure 9b         | 02_analysis/05_analysis_recruitment_exp_figures.do| 56-91       | figure9b.pdf  | 			   |
| Table 1 	    | 02_analysis/01_analysis_main_exp_tables.do        | 25-132      | table1.tex    | 			   |
| Table 2 	    | 02_analysis/01_analysis_main_exp_tables.do        | 133-264     | table2.tex    | 			   |
| Table 3           | 02_analysis/02_analysis_follow_up_tables.do 	| 28-175      | table3.tex    |                            |
| Table 4 	    | 02_analysis/01_analysis_main_exp_tables.do        | 265-395     | table4.tex    | 			   |
| Table 5 	    | 02_analysis/01_analysis_main_exp_tables.do        | 396-469     | table5.tex    | 			   |
| Table 6 	    | 02_analysis/05_analysis_recruitment_exp_tables.do | 19-121      | table6.tex    | 			   |
|-------------------|---------------------------------------------------|-------------|---------------|----------------------------|

Appendix outputs

|-------------------|---------------------------------------------------|-------------|------------------------|----------------------------|
| Figure/Table #    | Program                                      	| Line Number | Output file   	       | Note                       |
|-------------------|---------------------------------------------------|-------------|------------------------|----------------------------|
| Figure B1         | 02_analysis/01_analysis_main_exp_figures.do  	| 136-157     | appendix_figure1.pdf   |                            |
| Figure B2a        | 02_analysis/01_analysis_main_exp_figures.do  	| 158-175     | appendix_figure2a.pdf  |                            |
| Figure B2b        | 02_analysis/01_analysis_main_exp_figures.do  	| 176-184     | appendix_figure2b.pdf  |                            |
| Figure B2c        | 02_analysis/01_analysis_main_exp_figures.do  	| 185-193     | appendix_figure2c.pdf  |                            |
| Figure B3         | 02_analysis/02_analysis_follow_up_figures.do 	| 110-145     | appendix_figure3.pdf   |                            |
| Figure B4         | 02_analysis/02_analysis_follow_up_figures.do 	| 146-160     | appendix_figure4.pdf   |                            |
| Figure B5         | 02_analysis/01_analysis_main_exp_figures.do  	| 194-250     | appendix_figure5.pdf   |                            |
| Figure B6a	    | 02_analysis/02_analysis_follow_up_figures.do 	| 161-228     | appendix_figure6a.pdf  |                            | 
| Figure B6b	    | 02_analysis/02_analysis_follow_up_figures.do 	| 229-242     | appendix_figure6b.pdf  |                            | 
| Figure B6c	    | 02_analysis/02_analysis_follow_up_figures.do 	| 243-257     | appendix_figure6c.pdf  |                            | 
| Figure B6d	    | 02_analysis/02_analysis_follow_up_figures.do 	| 258-271     | appendix_figure6d.pdf  |                            | 
| Figure B7a	    | 02_analysis/02_analysis_recruitment_exp_figures.do| 96-159      | appendix_figure7a.pdf  |                            | 
| Figure B7b	    | 02_analysis/02_analysis_recuritment_exp_figures.do| 160-212     | appendix_figure7b.pdf  |                            | 
| Figure B8a        | 02_analysis/03_analysis_1st_online_svy_figures.do | 59-77       | appendix_figure8a.pdf  |                            |
| Figure B8b        | 02_analysis/03_analysis_1st_online_svy_figures.do | 59-77       | appendix_figure8b.pdf  |                            |
| Figure B9a	    | 02_analysis/01_analysis_main_exp_figures.do 	| 22-43       | appendix_figure9a.pdf  |                            | 
| Figure B9b	    | 02_analysis/03_analysis_1st_online_svy_figures.do | 78-96       | appendix_figure9b.pdf  |                            | 
| Figure B9c	    | 02_analysis/03_analysis_1st_online_svy_figures.do | 78-96       | appendix_figure9c.pdf  |                            | 
| Figure B9d	    | 02_analysis/04_analysis_2nd_online_svy_figures.do | 89-102      | appendix_figure9d.pdf  |                            |
| Table B1	    | 02_analysis/02_analysis_follow_up_tables.do	| 179-266     | appendix_table1.tex    |			    |
| Table B2 	    | 02_analysis/02_analysis_follow_up_tables.do	| 267-347     | appendix_table2.tex    |			    |
| Table B3 	    | 02_analysis/02_analysis_follow_up_tables.do	| 685-788     | appendix_table3.tex    |			    |
| Table B4 	    | 02_analysis/02_analysis_follow_up_tables.do	| 443-591     | appendix_table4.tex    |			    |
| Table B5 	    | 02_analysis/02_analysis_follow_up_tables.do	| 592-684     | appendix_table5.tex    |			    |
| Table B6 	    | 02_analysis/02_analysis_follow_up_tables.do	| 348-442     | appendix_table6.tex    |			    |
| Table B7 	    | 02_analysis/01_analysis_main_exp_tables.do	| 474-592     | appendix_table7.tex    |			    |
| Table B8 	    | 02_analysis/01_analysis_main_exp_tables.do	| 593-714     | appendix_table8.tex    |			    |
| Table B9          | 02_analysis/03_analysis_1st_online_svy_tables.do  |             | appendix_table9.tex    |                            |
| Table B10         | 02_analysis/04_analysis_2nd_online_svy_tables.do  |             | appendix_table10.tex   |                            |
| Table B11         | 02_analysis/05_analysis_recruitment_exp_tables.do | 126-202     | appendix_table11.tex   |                            |
|-------------------|---------------------------------------------------|-------------|------------------------|----------------------------|



