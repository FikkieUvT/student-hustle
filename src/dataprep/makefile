INPUT = ../../gen/analysis/input
OUTPUT = ../../gen/dataprep/output
DATA = ../../gen/dataprep/data

all: $(DATA)/downloaded_data.csv $(INPUT)/private_room.csv $(INPUT)/combined_mean_data1.csv $(OUTPUT)/clean_data.rmd 

$(DATA)/downloaded_data.csv: download_files.R
	R --vanilla < download_files.R

$(INPUT)/private_room.csv: $(DATA)/downloaded_data.csv transform_data.R
	R --vanilla < transform_data.R
        
$(INPUT)/combined_mean_data1.csv: $(INPUT)/private_room.csv clean_data.R
	R --vanilla < clean_data.R
	
$(OUTPUT)/clean_data.rmd: $(DATA)/downloaded_data.csv 
	Rscript -e "rmarkdown::render('clean_data.rmd')"
