<!-- Improved compatibility of back to top link -->
<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <h3 align="center">Energy Consumption Forecasting with Prophet</h3>

  <p align="center">
    Forecasting hourly energy consumption using Facebook Prophet for optimal power grid management.
    <br />
    <a href="https://github.com/George-Forgey/Energy-Consumption-Forecast"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/George-Forgey/Energy-Consumption-Forecast">Report Bug</a>
    ·
    <a href="https://github.com/George-Forgey/Energy-Consumption-Forecast">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#project-overview">Project Overview</a></li>
    <li><a href="#features">Features</a></li>
    <li><a href="#technologies-used">Technologies Used</a></li>
    <li><a href="#installation">Installation</a></li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#data-preparation">Data Preparation</a></li>
    <li><a href="#modeling-approach">Modeling Approach</a></li>
    <li><a href="#evaluation-metrics">Evaluation Metrics</a></li>
    <li><a href="#results">Results</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

<!-- PROJECT OVERVIEW -->
## Project Overview

This project aims to forecast hourly energy consumption using historical data from the PJM Interconnection region. The primary goal is to ensure **effective grid management**, **reduce costs**, and maintain **power stability**. We employ **Facebook's Prophet** library, which is a time series model designed to capture seasonality, holiday impacts, and long-term trends.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- FEATURES -->
## Features

- 📊 **Time Series Forecasting**: Predicts future hourly energy consumption.
- 🔄 **Seasonal Adjustments**: Accounts for **daily**, **weekly**, **monthly**, and **yearly** seasonal variations.
- 🎉 **Holiday Effects**: Incorporates public holidays into the model for better predictions.
- 🛠️ **Grid Search Optimization**: Uses a **grid search** to tune Prophet model parameters for increased accuracy.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- TECHNOLOGIES USED -->
## Technologies Used

- **Python 3.8+**: The programming language used for implementation.
- **Pandas**: For data manipulation and processing.
- **NumPy**: For numerical operations.
- **Matplotlib**: For visualizing trends and results.
- **Facebook Prophet**: For time series forecasting.
- **Scikit-Learn**: For evaluating model performance metrics.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- INSTALLATION -->
## Installation

To set up the project locally, follow these steps:

1. Clone the repository:

    ```sh
    git clone https://github.com/George-Forgey/Energy-Consumption-Forecast.git
    cd Energy-Consumption-Forecast
    ```

2. Create a virtual environment:

    ```sh
    python -m venv env
    ```

3. Activate the virtual environment:

    - **Windows**:

      ```sh
      .\env\Scripts\activate
      ```

    - **Linux/macOS**:

      ```sh
      source env/bin/activate
      ```

4. Install required dependencies:

    ```sh
    pip install -r requirements.txt
    ```
5. Fix Library Dependency Issues:


    Throughout Prophet, there is a single instance where the function `np.float_` is used. This function was removed in
    the NumPy 2.0 release, but certain components of the sklearn.metrics library still depend on `np.float64`.
    To resolve this compatibility issue with Prophet, we simply replace the usage of `np.float_` with `np.float64`.
  
        Navigate to `env\Lib\site-packages\prophet\forecaster.py`
        
        Use ctrl + F to locate the single occurrence of `np.float_`
        
        Replace it with `np.float64`

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE -->
## Usage

1. **Prepare Your Data**: Ensure the input CSV file (`PJME_hourly.csv`) is present in the project directory.
2. **Run the Notebook**: Open `energy_forecast.ipynb` using **Jupyter Notebook** or **VSCode** to execute the code.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- DATA PREPARATION -->
## Data Preparation

The dataset (`PJME_hourly.csv`) consists of hourly electricity consumption data:

- **Data Filtering**: Data from **2017 onward** was used to focus on the most recent consumption trends.
- **Handling Duplicates**: Duplicate timestamps were removed.
- **Missing Values**: Filled missing values using forward-fill to maintain continuity.
- **Seasonality Tags**: Custom functions are used to classify data into **spring**, **summer**, **fall**, and **winter**.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MODELING APPROACH -->
## Modeling Approach

1. **Model Initialization**:
   - We use **Facebook Prophet** to capture the seasonal patterns and trends in energy consumption.
   - **Holiday and Seasonal Effects**: The model incorporates **holidays** and different seasonal components for higher accuracy.

2. **Grid Search Parameter Tuning**:
   - A **Grid Search** method was used to find the best parameters, maximizing the model's predictive power.
   - **Progress Saving**: Intermediate progress is saved for long-running parameter searches, allowing resumption in case of interruptions.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- EVALUATION METRICS -->
## Evaluation Metrics

- **Mean Absolute Percentage Error (MAPE)**: Used as the main metric for evaluating forecast accuracy. It measures the average error between predicted and actual values, expressed as a percentage.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- RESULTS -->
## Results

- The **best model** achieved a **MAPE of approximately 9.6%**, which reflects strong predictive performance.
- Holiday effects and seasonal adjustments significantly enhanced the model's accuracy.
- **Forecast Visualization**:

![Energy Consumption Forecast](https://github.com/George-Forgey/Energy-Consumption-Forecast/blob/main/assets/forecast.png)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Contributions are always welcome! Follow these steps:

1. **Fork** the repository.
2. **Clone** your fork:

    ```sh
    git clone https://github.com/George-Forgey/Energy-Consumption-Forecast.git
    ```

3. **Create your Feature Branch**:

    ```sh
    git checkout -b feature/YourFeature
    ```

4. **Commit your Changes**:

    ```sh
    git commit -m 'Add your feature'
    ```

5. **Push to the Branch**:

    ```sh
    git push origin feature/YourFeature
    ```

6. **Open a Pull Request**.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->
## License

Distributed under the **MIT License**. See `LICENSE` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

**Project Maintainer**: [George Forgey](https://github.com/George-Forgey)  
**Email**: [gcforgey@gmail.com](mailto:gcforgey@gmail.com)

Project Link: [https://github.com/George-Forgey/Energy-Consumption-Forecast](https://github.com/George-Forgey/Energy-Consumption-Forecast)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/George-Forgey/Energy-Consumption-Forecast.svg?style=for-the-badge
[contributors-url]: https://github.com/George-Forgey/Energy-Consumption-Forecast/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/George-Forgey/Energy-Consumption-Forecast.svg?style=for-the-badge
[forks-url]: https://github.com/George-Forgey/Energy-Consumption-Forecast/network/members
[stars-shield]: https://img.shields.io/github/stars/George-Forgey/Energy-Consumption-Forecast.svg?style=for-the-badge
[stars-url]: https://github.com/George-Forgey/Energy-Consumption-Forecast/stargazers
[issues-shield]: https://img.shields.io/github/issues/George-Forgey/Energy-Consumption-Forecast.svg?style=for-the-badge
[issues-url]: https://github.com/George-Forgey/Energy-Consumption-Forecast/issues
[license-shield]: https://img.shields.io/github/license/George-Forgey/Energy-Consumption-Forecast.svg?style=for-the-badge
[license-url]: https://github.com/George-Forgey/Energy-Consumption-Forecast/blob/main/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/George-Forgey

Adding the `#readme-top` anchor at the very beginning ensures that all the "back to top" links have a valid target and work as intended.
