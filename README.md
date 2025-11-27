# Design-of-FIR-Filters-using-rectangular-window
#         DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of low pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```
clc;
clear;
close;

// Filter specifications
N = 25;                // Filter length
wc = 0.4 * %pi;        // Cutoff frequency (in radians)

// Initialize impulse response
h = zeros(1, N);
alpha = (N - 1) / 2;   // Midpoint

// Compute impulse response (ideal low-pass filter)
for n = 0:N-1
    if n == alpha then
        h(n+1) = wc / %pi;    // Handle division by zero at center
    else
        h(n+1) = sin(wc * (n - alpha)) / (%pi * (n - alpha));
    end
end

// Rectangular window → multiply by 1 (no change)
w = ones(1, N);
h = h .* w;

// Display impulse response
disp("Impulse Response h(n):");
disp(h);

// Plot impulse response
subplot(2,1,1);
plot(h);
title('Impulse Response h(n) using Rectangular Window');
xlabel('n');
ylabel('Amplitude');

// Frequency response
[H, w_freq] = freq(h, 512);

// Plot magnitude response
subplot(2,1,2);
plot(w_freq, abs(H));
title('Magnitude Response |H(ω)|');
xlabel('Frequency (rad/sample)');
ylabel('|H(ω)|');

```


# OUTPUT

<img width="1919" height="867" alt="image" src="https://github.com/user-attachments/assets/32a2c77f-9046-42e5-9d4f-6b1824a09793" />


# RESULT
Thus , generate design of low pass FIR digital filter using SCILAB are verified.
