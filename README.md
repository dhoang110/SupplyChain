# SupplyChain
#Step 1 & 2: Webscraping & arrange data on Postgres:
  - Install Postgres & PgAdmin4 
  - Create Server/Database: user: postgres, password: postgres
  - Create tables on database as in atm_scraping.sql file
  - Run ATM-webscrapping.ipynb notebook
  - Run subpage_details.ipynb notebook
  - Run subpage_reviews.ipynb notebook
  - Download reviews table as csv if you want. Done!

#Step 3: Organising relational database
  - Run the python script that connects to your warehouse
  - Scripts imports webscrapig data and transforms csv files in 2 relational files containing company details and their reviews

#Step 4: Arrange data on Elasticsearch: 
  - run the followings command in Bash:
    - cd elasticsearch
    - docker-compose up -d
    - docker cp elasticsearch-es01-1:usr/share/elasticsearch/config/certs/ca/ ./
  - access kibana from Docker or from any browser: http://localhost:5601
  - once in kibana User: elastic, Password : datascientest
  - create an Index name "atm_reviews"
  - run the bulk_script.py file to import the CSV data into Elasticsearch

#Step 5: Sentiment analysis
  - before running the script:
      - make sure important that you set-up the connection to elasticsearch and - run pip install elasticsearch vaderSentiment 
  - the pyhon script runs through each of the review and allocates its sentiment score and  label (positive, negative, neutral), then outputs dataframe with review id, company id, company name, review text, sentiment score and sentiment label
  