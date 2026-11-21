# AmbitionBox Company Data Web Scraping

A Python web-scraping project that collects company information from the [AmbitionBox company listings](https://www.ambitionbox.com/list-of-companies) and selected company review pages. The project uses `requests`, `BeautifulSoup`, and `pandas` to extract, organize, and save the data for analysis.

## Project Overview

The notebook demonstrates how to:

- Send HTTP requests to AmbitionBox company-listing pages.
- Parse HTML content with BeautifulSoup.
- Extract company names, overall ratings, review counts, industries, and city/location information.
- Collect company review-page links.
- Visit company review pages and extract available women’s and men’s review counts and ratings.
- Extract the “Highly Rated For” and “Critically Rated For” information when available.
- Store the collected information in a Pandas DataFrame and export it to a CSV file.

The main scraping script in the notebook is designed to process up to 500 listing pages, with up to 20 companies per page. It saves each page’s results immediately and can resume from the next page when the output CSV already exists.

## Dataset

The supplied dataset contains **720 company records across 36 listing pages** and has these columns:

| Column | Description |
|---|---|
| `Page` | Listing page from which the company was collected |
| `Company Name` | Company name |
| `Overall Rating` | Overall company rating shown on AmbitionBox |
| `Total Reviews` | Total review count shown on the listing |
| `Industry` | Company industry/category |
| `City` | Main city and additional locations shown on the listing |
| `Women Reviews` | Number of women’s reviews, when available |
| `Women Rating` | Women’s rating, when available |
| `Men Reviews` | Number of men’s reviews, when available |
| `Men Rating` | Men’s rating, when available |
| `Highly Rated For` | Categories in which the company is highly rated, when available |
| `Critically Rated For` | Categories in which the company is critically rated, when available |

**Dataset file note:** The uploaded file named `ambitionbox_full_dataset.xls` contains comma-separated CSV data, not an Excel workbook. Rename it to `ambitionbox_full_dataset.csv` before using it as a CSV file in Python or committing it to this repository.

## Technologies Used

- Python
- Jupyter Notebook
- Requests
- BeautifulSoup (`bs4`)
- Pandas
- HTML parsing

## Repository Structure

```text
.
├── Web-Scrapping1.ipynb          # Web-scraping notebook
├── ambitionbox_full_dataset.csv  # Scraped company dataset (rename supplied .xls file)
└── README.md                     # Project documentation
```

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/<your-username>/<your-repository-name>.git
   cd <your-repository-name>
   ```

2. (Optional) Create and activate a virtual environment:

   ```bash
   python -m venv venv
   ```

   Windows PowerShell:

   ```powershell
   .\venv\Scripts\Activate.ps1
   ```

   macOS/Linux:

   ```bash
   source venv/bin/activate
   ```

3. Install the required packages:

   ```bash
   pip install pandas requests beautifulsoup4 lxml jupyter
   ```

## How to Run

1. Start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

2. Open `Web-Scrapping1.ipynb`.
3. Run the cells in order.
4. The scraping workflow writes the collected records to `ambitionbox_full_dataset.csv` in the notebook’s working directory.

To load the supplied dataset after renaming it:

```python
import pandas as pd

df = pd.read_csv("ambitionbox_full_dataset.csv")
print(df.head())
print(df.info())
```

## Notes and Limitations

- Website HTML structure and CSS selectors can change. If AmbitionBox updates its pages, parts of the scraper may need to be adjusted.
- Some fields may be missing if the website does not display the information or if a request does not return the expected page content.
- The notebook includes request delays, but large scraping jobs can still take considerable time and may be restricted by the website.
- The notebook’s main scraping loop is configured for pages 1 through 500. The supplied dataset is a snapshot containing 720 records from 36 pages; it is not evidence that all 500 pages were scraped.
- Before running the scraper, check AmbitionBox’s current terms of use, robots.txt, and applicable rules. Use the data responsibly and do not overload the website.

## Disclaimer

This is an educational web-scraping project. AmbitionBox is the source website; this repository is not affiliated with or endorsed by AmbitionBox. Website content and ratings may change over time. Respect the website’s terms, access restrictions, and data-use policies.
