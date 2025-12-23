# CronSweeper 🧹

**CronSweeper** is a lightweight, automated utility designed to keep your system clean by periodically purging specified directories. It is perfect for managing temporary folders, download directories, or any location that accumulates "junk" files over time.

Built with Python, it tracks the amount of disk space reclaimed with every run, providing you with a detailed log of your storage savings.

## ✨ Key Features

*   **🗑️ Automated Cleanup**: Recursively removes all files and subdirectories in target locations.
*   **📊 Smart Logging**: Maintains a `log.csv` history of every cleanup, tracking total space freed (in MB).
*   **🛡️ Daily Safety Lock**: Automatically prevents multiple runs on the same day to avoid redundant processing.
*   **⚙️ Flexible Configuration**: Easily manage multiple target directories via a simple `.env` file.
*   **🪟 Windows Optimized**: Designed with Windows file systems in mind (handles `.pyw` execution and path parsing).

## 🚀 Getting Started

### Prerequisites

*   Python 3.6+
*   `pip` (Python package manager)

### Installation

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/sadmanhsakib/CronSweeper.git
    cd CronSweeper
    ```

2.  **Install Dependencies**
    ```bash
    pip install python-dotenv
    ```

3.  **Configure Environment**
    Create a `.env` file in the root directory. Add the `FOLDER_PATH` variable with the absolute paths of the folders you want to clean, separated by commas.

    **Example `.env`:**
    ```env
    FOLDER_PATH=C:\Users\Name\Downloads\Temp,C:\Windows\Temp\Junk
    ```
    > **⚠️ WARNING:** CronSweeper deletes **ALL** contents in these folders. Ensure you do not include important directories like your Desktop or Documents.

## 📖 Usage

### Manual Run
You can run the script manually to test your configuration:
```bash
python main.pyw
```

### Automating with Task Scheduler (Windows)
To make CronSweeper truly "set and forget," add it to Windows Task Scheduler:

1.  Open **Task Scheduler**.
2.  Click **Create Basic Task** and name it "CronSweeper".
3.  Set the **Trigger** to "Daily" or "Weekly".
4.  For **Action**, select "Start a program".
5.  **Program/script**: Browse to your `pythonw.exe` (usually in your Python installation folder).
6.  **Add arguments**: The full path to `main.pyw` (e.g., `C:\Path\To\CronSweeper\main.pyw`).
7.  **Start in**: The full path to the CronSweeper folder (e.g., `C:\Path\To\CronSweeper`).

## 📊 Log Format
The `log.csv` file tracks your cleanup history with the following columns:
*   `Lifetime-Counter`: Total number of times the script has run.
*   `Deletion-Date`: The date of the cleanup.
*   `Total`: Total space freed in that run (MB).
*   `[Folder Name]`: Space freed from each specific folder.

## 🤝 Contributing
This project is developed and maintained solely by **[Sadman Sakib](https://github.com/sadmanhsakib)**.

Contributions are welcome! If you have ideas for cross-platform support or better logging, feel free to fork the repo and submit a pull request.
