# TPA_QC_DATA
TPA QC data for comparative studies.
<html>

<head>
<title>TPA_QC_Data</title>
</head>

<body>

<p> This code is written to fetch the QC values from LIMS .csv files which was saved in a public folder.  LIMS dB doesn't store QC values.  TPA team asked for the QC values for doing comparision of QC valurs accross the years.  Assay file in .csv format taken year-wise from //Greenfinch folder and saved in a public folder.</p>
<!--begin.rcode
#Set working directory
path = "Z:/GET/PUBLIC/LIMS/QC_2014"
#pattern argument to fetch .csv
list.files(pattern=".csv$") 
# creating a list 
list.filenames<-list.files(pattern=".csv$")
#Check the list
list.filenames
#to retrive file names for downstream work
filenames <- paste(path, list.files(path=path), sep="/") 
#read all .csv files as one dataframe with the filenames
finalData<-do.call("rbind", sapply(filenames, read.csv, simplify = FALSE))
#to view the data
View(finalData)
#Fetching only the positive QC's
raghuFinal<-finalData[grep("G4", finalData$Well), ]
#to view the data
View(raghuFinal)
#date cleanup for final output
raghuFinal<- raghuFinal[ , -which(names(raghuFinal) %in% c("X","X.1",	"X.2",	"X.3","X.4","X.5","X.6","X.7",	"X.8","X.9","X.10","X.11","X.12"))]
#final output in the set directory.  Make sure to change the file name for each run.
write.csv(raghuFinal,"QC_2014.csv")
#This is an R HTML document. When you click the <b>Knit HTML</b> button a web page will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this
end.rcode-->

<!--p>You can also embed plots, for example:</p-->

<!--begin.rcode fig.width=7, fig.height=6

end.rcode-->

</body>
</html>

