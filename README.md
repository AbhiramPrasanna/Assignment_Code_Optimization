
---

# Satellite Position Calculation using Distributed Computing with Dask

## Overview

This project aims to efficiently calculate satellite positions from TLE (Two-Line Element) data using distributed computing with Dask. The code is designed to handle large datasets and reduce computation time by leveraging parallel processing across multiple CPU cores.

## Requirements

- Python 3.x
- numpy
- pandas
- sgp4
- pyproj
- dask
- dask.distributed

You can install the required packages using pip:

```bash
pip install numpy pandas sgp4 pyproj dask distributed
```

## Usage

1. **Data Preparation**:
   - Place your TLE data file in the specified path.
   - Modify the `tle_file` variable in the script to point to your TLE data file.
   - Adjust the `start_date` and `end_date` variables in the script to define the time range for position calculations.

2. **Running the Script**:
   Execute the script using jupyter notebook

   The script will perform the following steps:
   - Load TLE data.
   - Calculate satellite positions using the SGP4 library.
   - Convert ECEF coordinates to latitude, longitude, and altitude.
   - perform certain code optimizations
   - Filter positions based on user-defined geographic boundaries.
   - Save the results to a CSV file (`satellite_positions.csv`)
     
## Optimization Details

### Distributed Computing with Dask

- **Data Chunking**: The TLE data is divided into smaller chunks, allowing concurrent processing of each chunk. This reduces the overall time needed to process the entire dataset.

- **Parallel Task Execution**: Dask's distributed client manages the execution of tasks in parallel across available workers. Each worker processes a chunk of the TLE data, calculating satellite positions simultaneously.

- **Asynchronous Processing**: Using Dask's `as_completed`, the script starts processing results as soon as they are available, rather than waiting for all tasks to complete. This further optimizes the computation time.

- **Resource Management**: Dask efficiently manages CPU and RAM usage, distributing tasks based on available resources. This ensures that the system is not overwhelmed, and tasks are processed in an optimal manner.

  #### for more details on my approach in solving this problem statement kindly refer to this google colab link : https://colab.research.google.com/drive/1UxiRL-aAwjLzY6SuQvyKnnVoAfwAVjt8?usp=sharing

## License

This project is licensed under the MIT License.

---

