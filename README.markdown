# DilationSim.py: Unraveling Time Dilation in 4D and 5D

Hey there! Welcome to `DilationSim.py`, a Python script I crafted to explore the fascinating concept of time dilation on a spinning disk, “Five-Dimensional Time Dilation on a Spinning Disk.” Imagine a 1-meter carbon fiber disk whirring at 1500 m/s, fitted with super-precise thorium-229m nuclear clocks. This code simulates that setup to test whether a fifth dimension, inspired by the Randall-Sundrum model, tweaks time dilation in ways we can measure.

## What’s the Big Idea?

This script powers simulations for a 16U CubeSat experiment in low Earth orbit, designed to probe whether a warped fifth dimension amplifies time dilation beyond what standard 4D relativity predicts. Those thorium-229m clocks, with their incredible 1 × 10⁻¹⁹ s precision, measure tiny time shifts across the disk. The code adds real-world noise, fits parameters, and compares 4D and 5D models to see if there’s evidence of something extra-dimensional going on.

## What It Does

- **4D Time Dilation**: Computes the classic \(\gamma = 1/\sqrt{1 - v^2/c^2}\) for a spinning disk.
- **5D Time Dilation**: Models a warping effect with \(e^{-k y}\), testing warp factors from 10⁷ to 3 × 10⁷ m⁻¹ and an extra-dimensional size of 1.6 × 10⁻¹² m.
- **Realistic Noise**: Adds Gaussian and sinusoidal noise (7 × 10⁻¹⁹ s) to mimic clock jitter and vibrations.
- **Parameter Fitting**: Uses SciPy’s `curve_fit` to estimate 5D model parameters (\(a\), \(b\)).
- **Output**: Provides RMSE for 4D and 5D models, plus fitted parameters with 95% confidence intervals.

## What You Need to Run It

- Python 3.8 or later
- NumPy (for crunching numbers and generating noise)
- SciPy (for curve fitting)
- Python’s built-in logging (to track any hiccups)

Install the dependencies with:

```bash
pip install numpy scipy
```

## How to Get Started

1. Save the script as `DilationSim.py`.
2. Ensure NumPy and SciPy are installed.
3. Run it from your terminal:

```bash
python DilationSim.py
```

The script runs 20 simulations for each warp factor (10⁷, 2 × 10⁷, 2.5 × 10⁷, 3 × 10⁷ m⁻¹) and prints a clear summary. Here’s an example of the output:

```
Simulation Results Summary:
Warp Factor k = 2.5e+07 1/m
4D RMSE: 1.156e-05
5D RMSE: 3.920e-10 +/- 7.505e-11
Fitted a: 1.600e-12 +/- 1.940e-17 m
Fitted b: -5.014e-11 +/- 1.141e-10
```

## Understanding the Output

- **4D RMSE**: The error for the standard 4D model (no warping).
- **5D RMSE**: The average error for the 5D model, typically ~30,000x smaller than 4D.
- **Fitted a, b**: Parameters for the 5D warping effect, with error bars to show how certain we are.

## Why This Matters

This code supports our *Physical Review Letters* paper and a proposed CubeSat mission to test 5D time dilation in orbit. The 5D model’s RMSE (~3.920 × 10⁻¹⁰ s) is dramatically lower than the 4D model’s (~1.156 × 10⁻⁵ s), suggesting we might actually detect extra-dimensional effects. If confirmed, this could refine GPS timing or open new doors in fundamental physics.

## A Few Things to Know

- **Clock Precision**: We’re relying on thorium-229m clocks hitting 7 × 10⁻¹⁹ s precision, based on recent research [1].
- **Reproducibility**: Fixed seeds (`np.random.seed(run + 1)`) ensure consistent results.
- **Explore More**: Find the full dataset and code at [github.com/GautiEinarsson/DilatationSim](https://github.com/GautiEinarsson/DilationSim).
- **Troubleshooting**: If curve fitting fails (it happens sometimes), the script logs a warning and keeps moving.

## References

1. Ludlow, A. D., et al. (2015). *Reviews of Modern Physics*, 87, 637.
2. Randall, L., & Sundrum, R. (1999). *Physical Review Letters*, 83, 3370 & 4690.
3. Peik, E., et al. (2015). *Quantum Science and Technology*, 1, 015001.

## Let’s Connect

Got questions or want to geek out about spacetime? Email me at [gauti.boknair@gmail.com](mailto:gauti.boknair@gmail.com). Let’s push the boundaries of physics together!
