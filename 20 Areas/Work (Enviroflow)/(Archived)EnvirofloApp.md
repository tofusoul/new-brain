---
title: Archived Content from Enviroflo App
date: 2023-10-12
---
>  archived content from [[Enviroflow App]]
> remove some of the clutter -> 

- ~~[ ] Try Connect to Xero without the example app by either:~~
		- ~~[ ] the method in [this Guide](https://python.plainenglish.io/connect-xero-oauth-2-0-using-python-without-a-website-86c79474c482)~~ 
		- [ ] ~~or with the [PKCE Credentials](https://github.com/freakboy3742/pyxero#using-pkce-credentials) in this library~~

- Todos: 
- [x] In the subcontract generator, allow removal of quote that are not related to the project 
## Infrastructure
- ~~[ ] write a function to fetch costs from xero and feed it directly to the data store~~ too much noise, easier to get the report and update it like we currently do with quotes 
- [x] refactor the dataflow and model, so it's easy to get back into after the break 
- [x] model should be built and shared between the pages via the session state on data load 
- [x] shift the data storage to another service (google sheets is too slow) 
    - ended up using just the flat flies. 
- [x] Set up Git 
- [x] setup VS code for Jupyter Notebook development 
CANCELED ~~write a function to update the google sheet files directly from the flask app~~
- [x] install libraries 
    
## Data Wrangling
- CANCELED ~~build a file systems datastore with the same structure as the model~~
- [x] move away from the build-dfs function workflow 
- [x] create the derived tables that are currently in use 
- CANCELED ~~Re-Build DB.py~~
- [x] directly access the trello class that mike wrote to update the trello data
- [x] use session states on the tabs to control the page flow.
- [x] more feedback form
- [x] Clean and parsed data 
- [x] Fix problem with item columns 
- [x] make some wrapper classes around the data 
- [x] Get Quotes out of Simpro 
    - Ended up just copying the files from a zsh command off google drive.

## Project Management
- [x] move the roadmap onto Trello [[2023-06-02 Thursday]]
- [x] share github code to mike [[2023-06-02 Thursday]] 
- [x] push repo up to github 
- [x] Setup the dev environment locally 

## Design
- [x] work backwards from design goals to figure out what we need ✅ 2024-06-21

## Security
- [x] Purge the gs cred.py from repo history has the keys 
- [x] check the credential file from Mike is purged, not sure if my purge worked 

## Documentation
- [x] fix the ipynb readmes so they will run in the documentation folder 

## Tests
- [x] Test over the whole set of PDFs 
- [x] create an initial set of test of how things work across Algorightms
	 ✅ 2024-06-21






- [x] Get the collection of simpro quotes. 

1.  [x] filtered the pdfs by the mata-data.

- [x] Figure out the best ways to scrape the PDF 

1.  tabula is still the best thing

- [x] do a proper parse and export to Data frames on 2 pdf 

1.  [x] Get the quote table into dataframe

2.  [x] get the customer info into data frame

3.  [x] split the columns that didn\'t get parsed properly

4.  [x] turn the scrapping algorithm into a python Class

5.  [x] change how the quote meta info is gathered from (the table Location is not reliable) [[2023-05-27 Friday]]

6.  [x] clean and properly type the data

    1.  [x] clean up the line read of the data [[2023-05-27 Friday]]

    2.  [x] get the quote value by its relationship to the sub-total item in the column

        1.  [x] drop the irrelevant columns

    3.  [x] clean up the multi lines

- [x] Read one quote into Xero 

1.  [x] Authentication

2.  [x] pull the line items from the data

- [x] Handle VOs in quotes 

- [x] get projections to Joe from pipemedic [[2023-10-26 Wednesday]] TODO finish the broad strokes systems design #This~Week~ [2022-10-20 Thursday](../journals/2022_10_20.org) [2022-10-21 Friday](../journals/2022_10_21.org) 

- [x] build a python class for accessing the data on the spreadsheet in natural way 

- [x] start with how I want to access it 

1.  figure this out first, this maybe why you have been so unproductive in the past few days

    \*
