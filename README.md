# merger-data-extractor

The following artefacts are used to
- download/scrape, 
- extract by the means of NLP, and
- save in a structured way

the data on the merger cases from the European Commision's competition policy website. The information in the decision texts are only extracted for merger cases in English.

## Setup
For the artefacts to wokr as intended the following programs have to be installed:
- Python
- Google Chrome web browser

Additionally, the following python packages have to be installed as well:

- from selenium import webdriver
- from selenium.webdriver.chrome.options import Options
- import random
- import time
- from selenium.webdriver.common.action_chains import ActionChains
- from selenium.webdriver.common.keys import Keys
- from datetime import datetime
- import json
- import os
- import requests
- import pdfplumber
- from tqdm import tqdm
- import re
- import spacy
- from spacy.tokens import DocBin
- import random

A directory with the following structure has to be created:

![grafik](https://user-images.githubusercontent.com/55591730/170620307-658660b8-b4ff-4725-b85c-37081b1a680f.png)

Additionally, the newest chrome driver needs to be downloaded from https://chromedriver.chromium.org and saved in the directory "01_Web_Scraper". The chrome driver (chromedriver.exe) needs to be the same version as the installed Google Chrome web browser.

## Usage
 1. Run the web scraper
    1. Copy and rename the generated JSON-file to "raw_data.json" and save it in the folder "02_Data_Cleaner"
2. Run the data cleaner
    1. Copy and save the file "clean_train_data.json" in the folder "03_Data_Labeler"
    2. Copy and save the file "clean_input_data.json" in the folder "04_Text_Categorizer"
4.  If you wanna use the already trained model skip this step. But, if you wanna create your own model with your own training and evaluation data run the data labeler.
    1. Create your training and evaluation data and save it as "final_train_data.json" and "final_valid_data.json" in the folder "04_Text_Categorizer"
    2. Run the function "create_training_data" in the text categorizer
    3. Run the function "create_config" in the text categorizer
    4. Run the function "train_model" in the text categorizer
6.  Run the function "text_categorizer" in the text categorizer
    1. Copy and save the file "sentence_data.json" in the folder "05_Span_Categorizer"
8.  If you wanna use the already trained model skip this step. But, if you wanna create your own model with your own training and evaluation use the following steps.
    1. Create your training and evaluation data and save it as "train_data.json" and "valid_data.json" in the folder "05_Span_Categorizer"
    2. Run the function "create_training_data" in the span categorizer
    3. Run the function "create_config" in the span categorizer
    4. Run the function "train_model" in the span categorizer
9.  Run the function "span_categorizer" in the span categorizer
