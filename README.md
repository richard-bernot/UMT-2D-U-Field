2D U-Field Simulation

A deterministic, history-dependent 2D scalar lattice simulation used to study emergent regime behavior under local contrast, recursive redistribution, and decoherence.

The notebook is self-contained and can be run directly in Google Colab. Detailed implementation notes are included as comments throughout the code.

Running the Simulation

Open the .ipynb notebook in Google Colab.

Run the Solver definitions cell.

Set the desired parameters in the Run simulation cell.

Run the simulation cell.

Optionally run Export MP4 to generate an animation of the U-field evolution.

The simulation reports a final validation check and a summary of the completed run.

Primary Settings

The main run parameters are defined through Config:

grid_h, grid_w — lattice dimensions.

steps — number of resolved state updates.

w — rolling history window. Values of 3 or greater are supported; the baseline is 6.

alpha — steepness of the activation response.

rho_c — activation midpoint.

u0 — magnitude of the initial central perturbation.

seed_sign — sign of the initial perturbation: 1 or -1.

lambda_delta — weight of the local contrast response.

lambda_flux — weight of recursive redistribution.

lambda_decoherence — weight of decoherence/damping.

operator_mode — "matched" for the isotropic matched operator pair or "naive" for the axis-aligned comparison operator.

Baseline motion-law weights are:

lambda_delta = 1.00
lambda_flux = 0.50
lambda_decoherence = 0.25

A typical full run uses:

grid_h = 300
grid_w = 300
steps = 1000
w = 6
alpha = 10.0
rho_c = 0.5
u0 = 1e-3
seed_sign = 1
operator_mode = "matched"

Output

sim.run() returns the final state and principal diagnostic fields, along with stored summaries and visualization frames.

To export the stored U-field evolution as an MP4:

sim.export_u_mp4()

Frame capture frequency, animation frame rate, filename, and display scaling can also be adjusted through Config.

Note: A simulation step represents resolved state succession within the model and should not be interpreted as a physical unit of clock time.

License

Released under the GNU General Public License v3.0 (GPLv3).
