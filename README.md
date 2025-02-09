# Trakt to IMDb List Importer

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**Effortlessly transfer your movie and TV show lists from Trakt to IMDb custom lists.**

This tool simplifies the process of creating IMDb custom lists from your Trakt data. Export your lists from Trakt as CSV files using [TraktRater](https://github.com/damienhaynes/TraktRater).

-   **For movies, you can directly use the edited CSV file with the IMDb List Importer script.**
-   **For TV shows, this script will generate an IMDb-compatible CSV file.**

**To import the generated or edited CSV into IMDb, you will need to use the [IMDb List Importer Greasemonkey script](https://greasyfork.org/en/scripts/23584-imdb-list-importer).**

---

## Key Features

- Converts Trakt CSV exports to IMDb-compatible CSV format for TV Shows.
- Direct lookup using TMDb TV Show IDs for accurate IMDb ID retrieval for TV Shows.
- Handles large lists efficiently.
- Simple command-line interface for easy use (TV Shows only).
- Clear warning messages for potential data issues.

---

## Quick Start for Movies Only

If you're only importing movies, you can simplify the process:

1.  **Export your Trakt movie list to CSV using TraktRater.**
2.  **Edit the CSV:**  Remove all columns *except* the one containing the IMDb ID.
3.  **Rename the IMDb ID column header** to `Const`.
4.  **Import the edited CSV directly into IMDb using the IMDb List Importer script.  You *do not* need to run the Python script.**

---

## Prerequisites

Before using this script, ensure you have the following:

1.  **Python 3.x**: [Download Python](https://www.python.org/downloads/) if you don't already have it. (**Only required for TV Shows**)
2.  **`requests` Library**: Install the `requests` library using pip:
    ```bash
    pip install requests
    ```
    (**Only required for TV Shows**)
3.  **TMDb API Key**: Obtain a free TMDb API key from the [TMDb Developer site](https://developer.themoviedb.org/reference/intro/getting-started). You'll need to create an account and request an API key. (**Only required for TV Shows**)
4.  **Trakt CSV Export**: Export your Trakt lists (e.g., Watchlist, Custom Lists) to CSV using [TraktRater](https://github.com/damienhaynes/TraktRater).
5.  **IMDb Account**: You'll need an IMDb account to import the generated CSV file into a custom list.
6.  **Greasemonkey or Tampermonkey Browser Extension**: Required to run the IMDb List Importer script. See instructions below.

---

## What are Greasemonkey and Tampermonkey?

Greasemonkey (for Firefox) and Tampermonkey (for Chrome, Safari, Edge, etc.) are browser extensions that allow you to run custom JavaScript code on websites. This is needed to use the IMDb List Importer script, as IMDb does not natively support CSV imports.

-   [Greasemonkey (Firefox)](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/)
-   [Tampermonkey (Chrome, Safari, Edge, etc.)](https://www.tampermonkey.net/)

---

## Installing the IMDb List Importer Script

1.  **Install Greasemonkey (Firefox) or Tampermonkey (Chrome, Safari, Edge, etc.)** from the links above. Follow the instructions on the extension's page to install it in your browser.
2.  **Install the IMDb List Importer script**: Go to the [IMDb List Importer GreasyFork page](https://greasyfork.org/en/scripts/23584-imdb-list-importer) and click the "Install" button. Tampermonkey/Greasemonkey should automatically detect the script and prompt you to install it.

**Important Note for Firefox Users:** The author of the IMDb List Importer script has noted that it may not work in Firefox if the `privacy.firstparty.isolate` property in `about:config` is set to `true`.

---

## Getting a Trakt CSV Export Using TraktRater

1.  **Install TraktRater**: Follow the instructions on the [TraktRater GitHub page](https://github.com/damienhaynes/TraktRater) to install and set up TraktRater.
2.  **Authorize TraktRater with your Trakt account**: Run TraktRater and follow the prompts to authorize it to access your Trakt data.
3.  **Export your lists to CSV**: Use TraktRater's export functionality to export your desired lists (e.g., Watchlist, Custom Lists) to CSV files.

---

## CSV Preparation for TV Shows

**Important:** For TV shows, the script relies on TMDb IDs to accurately find the corresponding IMDb entries. Before running the script, you **must** edit the CSV file exported from TraktRater and remove all columns *except* these:

-   `tmdb_id` (This column MUST contain TMDb TV Show IDs)
-   `title`
-   `year`

These three columns are essential for the script to function correctly with TV shows.

---

## Installation (TV Shows Only)

These steps are **only required if you are importing TV Shows.**

1.  **Download the script**: Clone this repository or download the `trakt_to_imdb.py` script.
    ```bash
    git clone https://github.com/Divyansh8946/Trakt-to-IMDb.git
    cd Trakt-to-IMDb
    ```
2.  **Install the `requests` library**:
    ```bash
    pip install requests
    ```
3.  **Get a TMDb API Key**: Obtain your API key from the [TMDb Developer site](https://developer.themoviedb.org/reference/intro/getting-started) and replace the placeholder in the script:
    ```python
    tmdb_api_key = "YOUR_TMDB_API_KEY_HERE"
    ```
4.  **Place CSV files and script in the same directory**: Put your Trakt CSV export file and the `trakt_to_imdb.py` script in the same folder.

---

## Usage (TV Shows Only)

These steps are **only required if you are importing TV Shows.**

1.  **Update the script with your file paths**:
    -   Replace `INPUT_CSV_FILE_PATH_HERE` with the path to your Trakt CSV file.
    -   Replace `OUTPUT_CSV_FILE_PATH_HERE` with the desired path for the IMDb-compatible CSV file.

2.  **Run the script**:
    ```bash
    python trakt_to_imdb.py
    ```

3.  **Import the generated CSV into IMDb**:
    -   Use the [IMDb List Importer Greasemonkey script](https://greasyfork.org/en/scripts/23584-imdb-list-importer) to import the generated CSV file into your IMDb account.

---

## Configuration (TV Shows Only)

The script uses the following variables, which you can customize.  These are **only relevant for TV Show imports**:

-   `tmdb_api_key`: Your TMDb API key.
-   `trakt_csv_file`: Path to your Trakt CSV export file.
-   `imdb_csv_file`: Path to save the IMDb-compatible CSV file.
-   `tmdb_tv_id_column_name`: Column name in the CSV file containing TMDb TV Show IDs (default: `tmdb_id`).
-   `title_column_name`: Column name in the CSV file containing titles (default: `title`).
-   `year_column_name`: Column name in the CSV file containing release years (default: `year`).

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

---

## Acknowledgments

-   [TraktRater](https://github.com/damienhaynes/TraktRater) for enabling Trakt CSV exports.
-   [TMDb API](https://developer.themoviedb.org/) for providing movie and TV show data.
-   [IMDb List Importer](https://greasyfork.org/en/scripts/23584-imdb-list-importer) for enabling CSV imports into IMDb.

---

**Created by: Divyansh ([Divyansh8946](https://github.com/Divyansh8946))**
