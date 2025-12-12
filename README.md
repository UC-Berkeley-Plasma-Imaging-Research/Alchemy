# Alchemy: Abel Inversion Analysis Tool

Alchemy is a Python-based graphical user interface (GUI) designed for performing Abel inversions on 1D profiles extracted from 2D plasma images. It provides a comprehensive suite of tools for data extraction, preprocessing (smoothing, centering), and analysis using various Abel inversion methods provided by the PyAbel library.

## Features

*   **Data Loading**: Support for loading 2D images or 1D profiles from CSV and Text files.
*   **Data Extraction**:
    *   Interactive selection of rows from 2D data.
    *   Row averaging to improve signal-to-noise ratio.
*   **Preprocessing**:
    *   **Center Finding**: Automatic detection using Center of Mass or Gaussian Fit, with manual fine-tuning.
    *   **Cutoff Detection**: Automatic and manual definition of signal boundaries (left and right cutoffs).
    *   **Smoothing**: Apply Savitzky-Golay or Gaussian smoothing with customizable window sizes and polynomial orders.
    *   **Edge Tapering**: Option to taper signal edges to zero to reduce artifacts.
*   **Inversion Methods**:
    *   BASEX
    *   Hansen-Law
    *   Onion Peeling
    *   Three-Point
*   **Analysis & Visualization**:
    *   **2D Preview**: Visualize the raw data and the selected extraction region.
    *   **1D Profile**: View the extracted and smoothed profile with cutoffs and center marked.
    *   **Inversion Result**: Compare results from multiple inversion methods simultaneously.
    *   **Center Accuracy Test**: Systematically vary the center pixel to analyze the sensitivity of the inversion result (Average Density vs. Center).
    *   **Cutoff Accuracy Test**: Systematically vary the signal width to analyze the sensitivity of the inversion result (Average Density vs. Cutoff Delta).
    *   **Statistics**: Automatic calculation of Peak Density and FWHM.

## Installation

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/UC-Berkeley-Plasma-Imaging-Research/AbelInversions.git
    cd AbelInversions
    ```

2.  **Install Dependencies**:
    Ensure you have Python installed (3.8+ recommended). Install the required packages:
    ```bash
    pip install numpy matplotlib scipy PyAbel
    ```
    *Note: `tkinter` is required for the GUI and is usually included with standard Python installations. On Linux, you might need to install it separately (e.g., `sudo apt-get install python3-tk`).*

## Usage

1.  **Start the Application**:
    ```bash
    python Alchemy.py
    ```

2.  **Load Data**:
    *   Click **"Load CSV/Txt"** to open your data file.

3.  **Configure Extraction**:
    *   Use the **Row Index** field to select the line of sight to analyze.
    *   Use **Average +/- Rows** to average adjacent rows.

4.  **Set Analysis Parameters**:
    *   **Pixel Size**: Enter the physical size of a pixel in cm.
    *   **Center Pixel**: Click **"Auto"** or manually enter the center pixel index.
    *   **Cutoffs**: Enable "Width Cutoff" and click **"Auto Detect"** or manually set the Left and Right Cutoff pixels.
    *   **Smoothing**: Select a method (e.g., `savgol`) and adjust the Window (Win) and Polynomial (Poly) parameters for left and right sides.

5.  **Run Inversion**:
    *   Select one or more **Inversion Methods** (e.g., `basex`, `hansenlaw`).
    *   Click **"Update / Run Analysis"** (or press Enter).

6.  **Analyze Sensitivity**:
    *   Go to the **Center Accuracy** or **Cutoff Accuracy** tabs.
    *   Set the range and step size.
    *   Run the test to see how robust your result is to parameter variations.

## Project Structure

*   `Alchemy.py`: The main application script containing the GUI logic.
*   `backend/`: Directory containing backend logic.
    *   `abel_methods.py`: Helper functions for data processing, smoothing, and interfacing with PyAbel.
    *   `debug_abel_install.py`: A script to verify PyAbel installation and path.

## Requirements

*   Python 3.x
*   `numpy`
*   `matplotlib`
*   `scipy`
*   `PyAbel`
*   `tkinter` (usually built-in)
