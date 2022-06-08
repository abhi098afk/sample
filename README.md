## Introduction

This repository contains the codes to get shapefiles from PDF files by doing OCR,image processing and geocoding using PyGeos. The shapefiles obtained can be digitally mapped using QGIS.

Some results obtained:

1.
![picture](results(1).png)
2.
![picture](results(2).png)

# Prerequisites

- See requirements.txt for python packages to install.
- See the setup.sh for installing other dependencies and forming the correct file structure required for the program to run correctly.


# Installation

- Install QGIS : A Free and Open Source Geographic Information System.Linux and Windows implementation is provided here in this [download link](https://qgis.org/en/site/forusers/download.html).
- After installing Image Magick from the setup.sh, you will need to tweak its policy file a little bit.
- ImageMagick has some security policies disabling some rights for security reasons.
- The restricted policy is made to prevent unknown vulnerabilities coming from third party software as Ghostscript used here for PDF files. Be sure to update Ghostscript.

```
	#WRITE THIS IN YOUR TERMINAL:
	sudo nano /etc/ImageMagick-6/policy.xml
	
	#FIND AND EDIT THIS LINE BELOW:
	<policy domain="coder" rights="none" pattern="PDF" />
	
	#TO:
	<policy domain="coder" rights="read|write" pattern="PDF" />
```

## Folder Structure

Make sure you have both of the "files" and "Database" folders in the same location as your Main_app.py file.


# Usage

We are using Streamlit to make the web application. Streamlit is an open-source app framework for Machine Learning and Data Science teams to make web apps in minutes. 


- Make sure you have the files and Database folder empty before running the app.
- To run the app, simply open the terminal in your working directory and type :

```
	OMP_THREAD_LIMIT=1 streamlit run Main_app.py
```

## **Processing**

After taking the input from the user, multiple processes occur:

-Conversion of pages into pngs, optical character recognition to extract all the text in those pngs, table detection and creation.
-Tables extracted are then further analysed and addresses present in those tables are captured. 
-Addresses obtained are geocoded into lat/long coordinates which gives us the resultant shapefile of the PDF.



### **Time taken**

-Generally, a four page PDF takes up to 4-5 minutes to process and give the shapefile.
-A single page pdf takes up to 2 minutes.

