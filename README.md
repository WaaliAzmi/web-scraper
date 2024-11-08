# Web Scraping Tool for Contact Information and Social Media Links

This project is a Python-based web scraper designed to extract contact information (emails and phone numbers) and social media links (Facebook, Instagram, Twitter, and LinkedIn) from a list of websites. It uses Selenium for browser automation and `openpyxl` to manage data in Excel format.

## Features

- **Automated Web Scraping**: Uses Selenium to load websites, including dynamically loaded content.
- **Data Extraction**: Collects email addresses, phone numbers, and social media links.
- **Internal Link Crawling**: Traverses internal links to scrape additional pages, ensuring a thorough search.
- **Excel Output**: Saves extracted data to an Excel file, with each row corresponding to a website from the input list.
- **Error Logging**: Logs all scraping activities and errors for easy debugging.

## Prerequisites

- **Python**: Ensure Python 3.x is installed.
- **Dependencies**: Install required packages using the following command:
  ```bash
  pip install -r requirements.txt
  ```
  
- **ChromeDriver**: Download and place the appropriate `chromedriver` executable in your PATH, compatible with your Chrome version. [ChromeDriver download](https://sites.google.com/chromium.org/driver/)

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/WaaliAzmi/web-scraper.git
   cd web-scraper
   ```

2. **Setup Virtual Environment** (optional but recommended):
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows, use `.venv\Scripts\activate`
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Prepare the Input Excel File**:
   - Create an Excel file (e.g., `websites_list.xlsx`) with a list of websites in the first column starting from the second row.

## Usage

To run the scraper, use the following command:

```bash
python scraper.py
```

This will initiate the web scraping process, loading the websites from `websites_list.xlsx`, extracting contact information, and saving the data back into the Excel file.

### Example Command

```python
python scraper.py websites_list.xlsx
```

### Script Breakdown

1. **`load_websites_from_excel(file_name)`**: Loads the list of websites from an Excel file.
2. **`init_webdriver()`**: Initializes the Selenium WebDriver in headless mode.
3. **`scrape_website(driver, url)`**: Scrapes content from a specified URL.
4. **`extract_info_from_html(html_content)`**: Extracts emails, phone numbers, and social media links from the HTML.
5. **`find_internal_links(soup, base_url)`**: Finds internal links within a page for further scraping.
6. **`update_excel(sheet, row, emails, phones, social_media_links)`**: Writes extracted data back to the Excel file.

## Logging

The script creates a log file, `scraping_log.log`, capturing all scraping activities and errors, which helps with debugging and tracking the scraping process.

## Notes

- **Max Depth**: You can control how many internal links to follow by adjusting the `max_depth` parameter in the main function.
- **Headless Mode**: The WebDriver runs in headless mode by default for efficiency. To view the browser, remove the `--headless` argument in `init_webdriver()`.

## License

This project is open-source and available under the [MIT License](LICENSE).
