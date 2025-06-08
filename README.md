# Web-Server-Log-Analysis

Web Server Log Analysis – Calgary HTTP Dataset
📁 Overview

This project involves analyzing real-world web server logs from the University of Calgary using Python. The goal is to extract actionable insights from raw HTTP access logs by cleaning, transforming, and performing various analytical tasks on the data.
📦 Dataset Information

    Dataset Name: Calgary HTTP Access Logs

    Source: Lawrence Berkeley National Laboratory

    Download Link: ftp://ita.ee.lbl.gov/traces/calgary_access_log.gz

    Size:

        Compressed: ~5.4 MB

        Uncompressed: ~52.3 MB

    Format: Apache Common Log Format (ASCII text, 1 request per line)

🧹 Data Loading & Cleaning

    Loaded the compressed .gz file using Python's gzip and pandas.

    Parsed log lines using regular expressions to extract:

        Host

        Timestamp

        HTTP method, resource, protocol

        Status code

        Response size (bytes)

    Converted timestamp strings to datetime objects with pd.to_datetime().

    Cleaned and handled:

        Missing or malformed data

        Invalid byte values (e.g., -)

        Type conversions for numeric fields

        Extracted file extensions

🧪 Analysis Tasks & Outputs
Task	Description	Output Type
Q1	Count total HTTP log records	int
Q2	Count unique hosts (IP/domain)	int
Q3	Count of unique filenames per date (dd-MMM-yyyy)	dict[str, int]
Q4	Count of HTTP 404 Not Found responses	int
Q5	Top 15 filenames causing 404 errors	list[tuple[str, int]]
Q6	Top 15 file extensions causing 404 errors	list[tuple[str, int]]
Q7	Total bandwidth (bytes) per day in July 1995	dict[str, int]
Q8	Hourly request distribution (0–23 hrs)	dict[int, int]
Q9	Top 10 most requested filenames	list[tuple[str, int]]
Q10	Distribution of HTTP status codes	dict[int, int]
🛠️ Libraries Used

    pandas – Data manipulation

    gzip – Reading .gz compressed file

    re – Regular expression parsing

    datetime – Date/time parsing and formatting

⚠️ Common Issues & Fixes

    .dt accessor error: Ensure the timestamp column is properly converted using pd.to_datetime() before accessing .dt.

    SettingWithCopyWarning: Avoid chained assignment; use .loc or .copy() for safe assignments.

    Missing byte values: Filter out '-' or convert invalid bytes to NaN using pd.to_numeric(..., errors='coerce').

🧾 Sample Results

Q1: Total log records = 929261  
Q2: Unique hosts = 80666  
Q4: Total 404 responses = 10919  
Q5: Top 404 files = [('junk/missing.html', 421), ...]
Q7: Bandwidth (01-Jul-1995) = 7852341 bytes  
Q8: Requests at 13:00 = 5432  

📈 Output Visualizations (Optional)

Add plots using matplotlib or seaborn to visualize:

    Daily traffic trends

    Hourly request distribution

    404 error heatmap

    File extension frequency bar charts

✅ Conclusion

This project demonstrates the ability to work with large, unstructured server logs to uncover meaningful patterns using Python and data science skills. The codebase is modular, efficient, and handles various edge cases in real-world datasets.
