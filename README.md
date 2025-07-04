DilationSim.py: Simulating 4D and 5D Time Dilation

Welcome to DilationSim.py! This Python script powers the simulations for our Physical Review Letters (PRL) paper, exploring whether a fifth dimension tweaks time dilation on a spinning disk. It models time dilation for a 1-meter carbon fiber disk spinning at 1500 m/s, using thorium-229m clocks, based on the Randall-Sundrum 5D model. The code compares 4D and 5D time dilation, adds realistic noise, and fits parameters to test our hypothesis.

What It Does





Simulates 4D time dilation ((\gamma = 1/\sqrt{1 - v^2/c^2})) and 5D time dilation with a warping factor ((e^{-k y})).



Tests warp factors ((k = 10^7) to (3 \times 10^7 , \text{m}^{-1})), with extra-dimensional size ((y = 1.6 \times 10^{-12} , \text{m})).



Adds Gaussian and sinusoidal noise ((7 \times 10^{-19} , \text{s})) to mimic clock and vibrational effects.



Fits 5D model parameters ((a), (b)) using scipy.optimize.curve_fit.



Outputs RMSE for 4D vs. 5D models and confidence intervals for fitted parameters.

Dependencies





Python 3.8+



NumPy: For array operations and noise generation.



SciPy: For curve fitting (curve_fit).



Logging: Standard Python library for runtime warnings.

Install dependencies:

pip install numpy scipy

How to Run





Save the script as DilationSim.py.



Ensure NumPy and SciPy are installed.



Run the script:

python DilationSim.py

The script will:





Run 20 simulations per warp factor ((10^7, 2 \times 10^7, 2.5 \times 10^7, 3 \times 10^7 , \text{m}^{-1})).



Print a summary with 4D and 5D RMSE, fitted parameters ((a), (b)), and 95% confidence intervals.

Output

The script prints a summary for each warp factor, e.g.:

Simulation Results Summary:
Warp Factor k = 2.5e+07 1/m
4D RMSE: 1.156e-05
5D RMSE: 3.920e-10 +/- 7.505e-11
Fitted a: 1.600e-12 +/- 1.940e-17 m
Fitted b: -5.014e-11 +/- 1.141e-10





4D RMSE: Error for the 4D model (no warping).



5D RMSE: Error for the 5D model, showing ~30,000x improvement.



Fitted a, b: Parameters for the 5D warping effect, with confidence intervals.

Context

This code supports our PRL paper, “Five-Dimensional Time Dilation on a Spinning Disk.” It simulates time dilation for a disk experiment and a proposed CubeSat in low Earth orbit. The results (Table 1 in the paper) show the 5D model’s superior fit, suggesting extra-dimensional effects are detectable.

Notes





The thorium-229m clock precision ((7 \times 10^{-19} , \text{s})) is an estimate based on experimental work [Ludlow2015].



The code uses a fixed seed for reproducibility (np.random.seed(run + 1)).



If curve fitting fails (rare), warnings are logged.

Contact

Questions? Reach out to Gauti Einarsson at gauti.bokanir@gmail.com.
