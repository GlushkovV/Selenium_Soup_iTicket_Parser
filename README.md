# Selenium_Soup_iTicket_Parser

# Web scrapping: iTicket.uz

## Working out errors related to the start of the code
- If an error occurs when running the code after installing the necessary libraries, then most likely the Chrome web driver for your OS is not installed. How to install the web driver can be found at this link. [selenium-python](https://selenium-python.com/install-chromedriver-chrome?ysclid=ly2ufnhjip111135754)
- If the code does not work after installing the web driver or an error occurs, then you need to check whether the Chrome browser is open in memory. If so, you need to unload it (close it). This is due to the fact that the Chrome browser launched by the code runs in the background in the PC memory and may conflict with the Chrome browser running at the same time.
- If the error still occurs, then you need to check or reinstall the libraries you are using.

## Working with the parser
- To start parsing the site [iticket.uz](https://iticket.uz/ru/events) it is required to make a request with a call to the ItikcetUzParser().parser.events_site_parser() in this case, the parser collects site data from the "All events" section. When declaring a class, you can specify a link from another category, then the parser will collect data only for this category ItikcetUzParser('https://iticket.uz/ru/events/cultural-events').events_site_parser(). The parser outputs data in the Pandas Data Frame format in the format "as collected." 
- For data conversion, a separate class has been written that allows you to convert a frame into an easily interpreted Pandas Data Frame. To make a call, you need to make a request and, when declaring a class, pass the parser frame to the ‘input_df’ variable, as in the DataConverter(parsed_df).example.transformation(). 
- For convenience, you can combine these queries into one query that will immediately provide the resulting frame DataConverter(ItikcetUzParser().events_site_parser()).transformation(). 
- To save the resulting frame to a CSV file, you need to decompress a line of code cleared_df.to_csv(f"Selenium_Soup_iticket_{datetime.now().strftime('%d%m%Y')}.csv") which saves the data to a file named "Selenium_Soup_iticket_10072024.csv" and a folder with the code being run. The date will be inserted automatically - the current date of saving the parsing result.

## Important
- The parser does not collect event data from event pages that contain an active element id="icalendar", because without selecting a date, the class="accordions" element is not formed, without which parsing the page does not make sense. If it is necessary to parse such a page, you will need to add a parser class with a separate logic for processing the calendar element. At the moment, there is no such need

# Additionally
- This script is provided for educational and informational purposes only.
