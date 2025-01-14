# PythonSECProject
An analysis of SEC fillings, focused on D type forms (exempt offering of securities),
business focused application to identify macro-trends, startups to invest in, overview of the
exempt securities market, etc. Data sourced from SEC Edgar database.

Expectations: 
Ask for input from user: search by month or search by date?
Request given daily indices from SEC based on the user input:
	If user selects monthly, request the given month index
	If user selects by date, request all daily indices for the given date range (rand wait between requests)
Filter out everything but D form fillings
Parse resulting data into pandas
Based on the state column, plot state occurrences on a US map
	The more occurrences, the higher the color intensity
Ask for input from user: which state/states is user interested?
Filter out everything but requested states
Based on the resulting data frame, select columns relevant for lead generation: Company name, adress, telephone number, associated persons etc...
Print relevant dataset head
Ask for input from user: confirm data export (maybe we could add a modification option at this step? e.g.: "Would you like to add any of the following columns...")
Write a csv which is to be imported into a CRM used by user
