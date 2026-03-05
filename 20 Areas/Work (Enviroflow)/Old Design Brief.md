- Build it mostly in [[Python]]

- [Envoiroflo Server](./envoiroflo server.org) is setup to run through the orchastration

- [project plan at trello board](https://trello.com/b/bdm5Qh8y/app-issues-improvements)

- Does what the planning part of the spreadsheet does, but interacts

with [[SimPro]] data through their rest api

- also need to interact with the [[30 Resources/Programming & Development/Trello API]] and [[Xero]]

- Using [[Pandas]] for the Data Analytics

- Using [[Streamlit]] for ui

- Remember...

- No one cares about implementation details they just want it to work how they imagine it, even if it hasn\'t been communicated properlyi

- e.g. No-one cares where the data is stored, or how it\'s stored. they just want to be able to trust it.

- Why is...

- Everyting built in python

- initially the idea is to just use jupyter notebooks to write out all the logic, and then deliver the apps as static pyscript web apps, so there is no real security worries beyond making sure people don\'t copy the html file and share them whilly nilly

- Pyscript is just too new and breaking changes were happening left and right, it was just too much of a worry

- Every thing in dataframes

- The initial idea is just to realise my dream of an alternative to spreadsheets, where you can ensure a nice typed dataflow, while controlling inputs so things don\'t break

- This is kind of realised by now, but we just need to solidify it, and not forget why this is exciting

- The UI Written in streamlit

- Streamlit seems the fastest path to itterating UI with the code we already have.

- Even though it is still really new, it\'s not nearly as new as pyscript, and it has a simliar easy deployment path.

- The Data stored in google sheets.

- Again goes back to creating the ability to do what spreadsheets does for a business but making it stable and typesafe, with guardrails around the data input

- Using google sheets as a backend will allow us to do spread sheet things if we like, but the data sources are strict and typed etc.

- provides a familiar layer for me to examine the data we keep
