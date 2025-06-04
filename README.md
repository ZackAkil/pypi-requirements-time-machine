# PyPI Requirements Versioner [(try app)](https://zackakil.github.io/pypi-requirements-time-machine/)

This is a simple web application designed to help you generate a versioned `requirements.txt` file for your Python projects based on a specific historical date. It queries the official PyPI API to find the latest available version of each package on or before your chosen date, ensuring reproducibility for your project's dependencies at a past point in time.

## How to Use

1.  **Open the Application:** Open the `index.html` file (or the Canvas preview if you're running it in this environment).

2.  **Paste Requirements:** In the "Paste your requirements.txt:" text area, paste the contents of your unversioned `requirements.txt` file (e.g., just package names like `requests`, `numpy`, `flask`). The app comes pre-filled with example packages for quick testing.

3.  **Select Target Date:** Use the "Select Target Date:" input to pick a date in the past. The application will find package versions that were released on or before this date. It defaults to January 1, 2019, for easy testing.

4.  **Generate:** Click the "Generate Versioned Requirements" button.

5.  **View Output:**

    * The "Versioned requirements.txt:" text area will display the updated list of packages, each with its appropriate version pinned (`package==version`).

    * The "PyPI Release History Links:" section will show direct links to the release history page on PyPI for each package, allowing you to easily validate the retrieved versions.

## Features

* **Version Pinning:** Automatically adds exact version numbers (`==X.Y.Z`) to your Python packages.

* **Historical Accuracy:** Retrieves package versions based on a specific historical release date.

* **PyPI API Integration:** Utilizes the official PyPI JSON API for reliable package data.

* **Validation Links:** Provides direct links to PyPI's release history pages for easy verification of versions.

* **User-Friendly Interface:** Simple, responsive side-by-side layout with clear inputs and outputs.

* **Auto-filled Example:** Comes pre-loaded with example requirements for immediate testing.

## Technical Details

This application is built using standard web technologies:

* **HTML:** For the basic structure of the web page.

* **Tailwind CSS:** For modern and responsive styling.

* **JavaScript:** Powers the core logic, including:

    * Fetching package metadata from the PyPI JSON API (`https://pypi.org/pypi/<package_name>/json`).

    * Parsing the JSON response to extract release versions and their `upload_time_iso_8601` timestamps.

    * Filtering and sorting releases to determine the latest version available on or before the specified target date.

    * Dynamically updating the output text areas and generating clickable links.

* **PyPI JSON API:** Leverages PyPI's programmatic interface for reliable data retrieval, avoiding fragile web scraping.

## Important Considerations

* **API Politeness:** A small delay is introduced between each API call to avoid overwhelming PyPI's servers and reduce the likelihood of encountering rate limits. For very large `requirements.txt` files, the process might take some time.

* **Date Precision:** The application considers the earliest upload time of a package version as its "release date" for historical accuracy.

* **Error Handling:** Includes basic error handling for network issues or if a package is not found on PyPI.
