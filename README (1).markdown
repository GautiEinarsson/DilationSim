# Time Dilation Simulation

## Overview
This Python script (`DilationSim.py`) simulates time dilation effects in a hypothetical 5D spacetime model compared to a standard 4D relativistic model. It models a rotating disk with clocks at various radial positions, incorporating a fifth-dimensional warping effect parameterized by a warp factor. The simulation includes noise to mimic experimental conditions and uses curve fitting to estimate 5D parameters.

## Requirements
- Python 3.x
- NumPy
- SciPy
- Logging (standard library)

Install dependencies using:
```bash
pip install numpy scipy
```

## Usage
Run the script directly:
```bash
python DilationSim.py
```

The script will:
1. Simulate time dilation for a rotating disk with specified parameters.
2. Apply 4D and 5D time dilation models.
3. Add Gaussian and vibrational noise to the 5D data.
4. Perform curve fitting to estimate 5D warping parameters.
5. Output a summary of results, including RMSE for 4D and 5D models and fitted parameters.

## Key Parameters
- **Speed of light (`c`)**: 299,792,458 m/s
- **Disk edge speed (`v`)**: 1,500 m/s
- **Disk radius (`R`)**: 0.5 m
- **Fifth dimension size (`y_default`)**: 1.6e-12 m
- **Noise levels**:
  - Thorium-229m clock noise: 7e-19 s
  - Vibration noise amplitude: 7e-19 s
- **Warp factors**: [1.0e7, 2.0e7, 2.5e7, 3.0e7] 1/m
- **Number of runs**: 20 per warp factor
- **Radial points**: 200, from center to edge

## Methodology
1. **4D Time Dilation**: Calculated using the Lorentz factor, `gamma = 1 / sqrt(1 - v_r^2 / c^2)`, where `v_r` is the velocity at radius `r`.
2. **5D Time Dilation**: Extends the 4D model with an exponential warping term, `gamma * exp(-a_scaled * r + b)`.
3. **Noise**: Combines Gaussian noise and sinusoidal vibrational noise to simulate experimental imperfections.
4. **Curve Fitting**: Uses `scipy.optimize.curve_fit` to fit the 5D model to noisy data, estimating parameters `a_scaled` and `b`.
5. **Statistics**: Computes mean, standard deviation, and 95% confidence intervals for fitted parameters and RMSE.

## Output
The script prints a summary for each warp factor, including:
- **4D RMSE**: Root mean square error of the 4D model compared to noisy 5D data.
- **5D RMSE**: Average RMSE of the fitted 5D model with confidence interval.
- **Fitted Parameters**:
  - `a`: Scaling factor for the fifth dimension (with confidence interval).
  - `b`: Offset term (with confidence interval).

## Notes
- The script uses a fixed seed for reproducibility (`np.random.seed(run + 1)`).
- Curve fitting bounds are set to ensure stability (`±0.01%` for `a_scaled`, `±5e-10` for `b`).
- Logging is configured to warn about curve fitting failures.

## License
This project is unlicensed and provided as-is for educational purposes.