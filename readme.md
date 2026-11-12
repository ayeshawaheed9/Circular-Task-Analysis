# 📌 Circular Task Analysis – MouseReMoCo

## ✅ Project Overview

This project analyses data from a circular tracking task recorded with the MouseReMoCo software. We load the raw recordings, work out how the files are organised, reproduce the reference graphics, recompute the performance statistics, and then run the same code on a recording we made ourselves.

The work is split into three parts, each in its own notebook, so that every team member can work independently on their own branch. A single `main.ipynb` notebook ties everything together: running it executes all three sub-notebooks in order, displays their results, and exports everything as an HTML report (`main.html`).

**Goals**

- Understand how MouseReMoCo stores its data (the data file and the marker file).
- Reproduce the reference graphics using the provided files `001MoDe_R1.csv` and `001MoDe_R1.marker.csv`.
- Recompute the values from the table at the end of `001MoDe_R1.marker.csv`, using our own code on the data in `001MoDe_R1.csv`.
- Run our code on at least one file that we recorded ourselves with MouseReMoCo.

The statistics we compute are:

| Statistic | Meaning |
|-----------|---------|
| `nLaps` | Number of laps completed |
| `Re` | Effective radius |
| `Te` | Effective tolerance |
| `error` | Percentage of samples outside the target area |
| `MT/lap` | Movement time per lap |
| `IDe/lap` | Effective index of difficulty per lap |
| `Be` | Effective bandwidth |
| `IPe` | Effective index of performance |


## ✅ Repository Structure

```
├── data/                                  # Provided and self-recorded data files
│   ├── 001MoDe_R1.csv
│   ├── 001MoDe_R1.marker.csv
│   └── (our own MouseReMoCo recording(s))
├── notebooks/
│   ├── 01_reproduce_graphics.ipynb        # Part 1: reproduce the graphics
│   ├── 02_recompute_statistics.ipynb      # Part 2: recompute the statistics table
│   └── 03_own_data_analysis.ipynb         # Part 3: analysis of our own recording
├── main.ipynb                             # Runs all three notebooks and shows the results
└── README.md                              # This file
```

## ✅ Getting Started

1. **Clone the repository**

   ```bash
   git clone https://github.com/ayeshawaheed9/Circular-Task-Analysis.git
   cd Circular-Task-Analysis
   ```

2. **Install the dependencies**

   We use a conda Python environment with the following packages:

   ```bash
   conda install numpy matplotlib scipy ipykernel nbformat nbconvert
   conda install -c conda-forge ipympl
   ```

3. **Run the project**

   Open the repository folder in VS Code (with the Python and Jupyter extensions), open `main.ipynb`, select your conda kernel, and click "Run all". Running `main.ipynb` runs all the sub-notebooks in the `notebooks/` folder, and the results of every part are shown in the output. The last cell of `main.ipynb` saves the whole notebook as an HTML file (`main.html`) next to it and opens it in your web browser. The notebooks expect the data files to be in the `data/` folder.

   You can also open and run any single notebook from the `notebooks/` folder on its own.

## ✅ What Each Notebook Does

**`main.ipynb`**
- The entry point of the project.
- Runs `01_reproduce_graphics.ipynb`, `02_recompute_statistics.ipynb` and `03_own_data_analysis.ipynb` one after the other, so that all plots and tables appear in one place.
- Its last cell exports the notebook as `main.html` (with all the graphics, without cell numbers) and opens it in the browser. Cells tagged `hide` are left out of the HTML.

**`01_reproduce_graphics.ipynb`**
- Reads the data file and the marker file.
- Uses the markers to find where each record starts and stops.
- Reproduces the trajectory plots (points inside and outside the target) and the time-series plots (X, Y and the inside-target flag).

**`02_recompute_statistics.ipynb`**
- Computes `nLaps`, `Re`, `Te`, `error`, `MT/lap`, `IDe/lap`, `Be` and `IPe` from `001MoDe_R1.csv`.
- Compares the results with the table at the end of `001MoDe_R1.marker.csv`.

**`03_own_data_analysis.ipynb`**
- Applies the same processing and statistics to a recording made by the team with MouseReMoCo.
- Produces the plots and the statistics table for our own data.

## ✅ Expected Outputs

Running `main.ipynb` displays the following, and also saves it all as `main.html`:

- Trajectory and time-series plots for each analysed record.
- A statistics table for the provided data, checked against the reference values.
- A statistics table and plots for our own recording.

## ✅ Team Contributions

| Team member | Role | Contribution |
|-------------|------|--------------|
| **Ayesha Waheed** | Manager | Created and manages the repository, reviews and merges all pull requests. Part 1: reproducing the graphics (`01_reproduce_graphics.ipynb`). |
| **Charles Sam DEEMUA** | Team member | Part 2: recomputing the statistics table (`02_recompute_statistics.ipynb`). |
| **Albatoul Ahmad** | Team member | Part 3: analysis of our own MouseReMoCo recording (`03_own_data_analysis.ipynb`). |

**Workflow:** each person works on their own branch and in their own notebook. Changes reach `main` only through pull requests, which are reviewed by the team and merged by the manager.