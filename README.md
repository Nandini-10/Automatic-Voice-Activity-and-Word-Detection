# Automatic-Voice-Activity-and-Word-Detection

## Pre-emphasis
**File:** \`pre-emphasis.ipynb\`

### Overview
Pre-emphasis is equivalent to applying a high-pass filter to the sound source.

#### Formula
\`\`\`
H(z) = 1 - alpha/z = Y(z)/X(z)

y[n] = x[n] - alpha*x[n-1]
\`\`\`
Pre-emphasis reduces the impact of both lip radiation and glottal shaping on the sound, resulting in a less human-like quality.

#### Observations
- Sampling rate = 8000 Hz
- 30ms corresponds to 240 samples

#### Insights
- As the value of 'p' increases, the energy of the error signal decreases, indicating a more accurate approximation of the signal.
- A higher 'p' results in more precise estimation of formant frequencies and bandwidths.
- The reconstructed signal obtained by applying an impulse train to an LP filter closely resembles the original signal.

---

## Windowing
**File:** \`windowing.ipynb\`

### Overview
Output function is calculated in a similar way as CA-1A.

#### Windows Considered
- Rectangular
- Hamming

#### Observations
- Fundamental frequencies and harmonics estimated.
- Peaks in the spectrum become easier to distinguish with larger window sizes.
- Formant frequencies are easier to determine with smaller windows.
- Increasing F0 shifts the resonating frequency of the vocal tract.
- Hamming windows exhibit smaller side lobes compared to Rectangular windows.

---

## Speech Synthesis
**File:** \`speech synthesis.ipynb\`

### Overview
Given values of F1 and B1, theta and r are calculated to determine the poles of the filter.

#### Approach
- The filter is passed through an impulse response and a triangular pulse train to generate outputs.
- Various formant and pitch values are tested to analyze their effects.

#### Observations
- Increasing the number of formants results in different vowel sounds.
- Sound quality varies with different fundamental frequencies.
- Filters with more roots correspond to different vowel qualities.

#### Formulas
\`\`\`
Transfer function: H(z) = 1/(1 - r * exp(-jtheta))
Output function: y[n] = 2r*cos(theta)*y[n-1] - r^2*y[n-2]
\`\`\`

---

This README provides a high-level overview of the contents and analyses performed in the provided notebooks.
EOL

# Git commands to upload to GitHub
git add README.md
git commit -m "Add README for project overview"
git push origin main
