# Example waveforms that are featured throughout the paper
All waveforms are stored in MATLAB format, they are designed to yield b = 2 ms/µm2 at a minimal time given a maximal gradient amplitude and slew rate of 80 mT/m and 100 T/m/s. Loading any of these functions will generate a gradient waveform with supplementary information.

### Example:  
Calling the following in matlab
```
load('[pathToRepo]\Wong et al. (1995) STE_Max.mat')
```
will load the variables `gwf`, `rf` and `dt` into memory.  

`gwf` is the gradient waveform in a collum matrix (n-by-3) in units of T/m.  
`rf` is the spin dephasing direction as a function of time (n-by-1).  
`dt` is the duration of each step of the waveform in units of s.  

Note that `gwf` is stated in the physical gradient axis system. To get the effective gradient waveform, call `gwf_eff = gwf .* rf`.  

To plot the effective gradient waveform, see the function `gwf_plot_all(gwf, rf, dt)` in the [multidimensional diffusion toolbox](https://github.com/markus-nilsson/md-dmri), or call 

```
t = linspace(0, dt * size(gwf, 1), size(gwf,1));
plot(t, gwf .* rf)
ylabel('Gradient waveform [T/m]')
xlabel('Time [s]')
```
