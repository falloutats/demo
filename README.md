# README

## homedepot_data.py

This is a `Python` script for web scraping using the Scrapy framework. It defines a spider named "Data" that is used to scrape pricing information for products from a retail website.

The spider starts by prompting the user to enter a name for the output file. It then defines a dictionary called "cmp" that will be used to store the scraped data. The spider then defines a method called "closed" that will be called when the spider is finished. The "closed" method creates a Pandas dataframe from the data in the "cmp" dictionary and writes it to an Excel file with the name entered by the user.

The spider then defines a method called "start_requests" that is used to generate a list of URLs to scrape. The URLs are generated by combining a list of product IDs with a list of zip codes, and then using a formatted string to create the final URL. The spider then sends a request to each URL using the Scrapy framework.

The spider defines a method called "parse" that is used to parse the response from each URL. The method extracts the store ID from the JSON response and uses it to send a second request to an API endpoint. The method then passes the response to a method called "parse_detail".

The "parse_detail" method extracts the product name and pricing information from the JSON response and stores it in the "cmp" dictionary.

Finally, the spider logs the number of products that have been scraped using the Scrapy framework.

Overall, this script demonstrates how to use the Scrapy framework to scrape data from a retail website and store it in a Pandas dataframe.


## TP_1.py 

The `def main()` function is a part of a `Python` script that performs data manipulation tasks on an Excel workbook (`location.xlsx`). The script uses `pandas` and `openpyxl` libraries for loading data from an `Excel` file and modifying it.

The `main()` function is not called in the script, so it has to be called explicitly by the user to execute its content. The function reads data from the `data.xlsx` file using `pandas.read_excel()` method and loads the `location.xlsx` file into the script using the `openpyxl.load_workbook()` method.

The function then calls data_splitter() function to extract city and state names from the sheet names within a specific range (from sheet 31 to 165). The extracted names are then used in a loop to fetch data from the df DataFrame using the fetch_data() function. If the data is empty, nothing happens. Otherwise, the match() function is called, which applies some data manipulations on the sheet corresponding to the current iteration of the loop.

After all the iterations, the modified workbook is saved to a new file (test_final.xlsx) using the wb.save() method.

Functions used in the def main() function:
fetch_data(filer_by_state=None, filter_by_city=None, info=False) function

The fetch_data() function fetches data from the df DataFrame based on the input city and state names. The function returns a DataFrame after applying a filter on the df DataFrame using the city and state names.

The function has three parameters:

filer_by_state: a string that represents the state name to filter the df DataFrame.
filter_by_city: a string that represents the city name to filter the df DataFrame.
info: a boolean value that determines whether to display the shape of the df DataFrame or not.
match(filter_data,index=31, reveal=True) function

The match() function performs data manipulation on the sheet corresponding to the input index. The function applies some data manipulation on the sheet, such as changing the values of specific columns based on some conditions. The function returns a string that describes the total number of iterations of the loop.

The function has three parameters:

filter_data: a DataFrame that contains the data that needs to be matched with the data in the Excel sheet.
index: an integer that represents the index of the sheet that needs to be modified.
reveal: a boolean value that determines whether to display some information or not.
data_splitter(sheet_names) function

The data_splitter() function extracts city and state names from the sheet names and returns them as a list.

The function has one parameter:

sheet_names: a list of names of sheets within a workbook.
Example usage
To use the def main() function, you need to call it explicitly by adding main() at the end of the script. For example:


    if __name__ == '__main__':
        import openpyxl
        import pandas as pd
        import time

        file_with_data = '/Users/fallout/PycharmProjects/union_rates_time_series/data.xlsx'
        target_file = '/Users/fallout/Downloads/location.xlsx'

        ####################################################################################################################

        tick = time.time()
        df = pd.read_excel(file_with_data)
        wb = openpyxl.load_workbook(target_file)
        tock = time.time()
        city_state_index = 0
        print(f'{tock - tick} seconds, to open the file')

        city, state = data_split

