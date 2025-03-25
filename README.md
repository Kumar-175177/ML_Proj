# ML_Proj
Target Voice Separation Using Deep Neural Networks
Project Overview
This project focused on developing a voice filter to enhance a speaker's voice by reducing background noise. The implemented model utilized LSTM and Bi-LSTM networks, which were fine-tuned for hyperparameter optimization. To improve performance, the audio length for training was extended from 3 to 10 seconds.
LSTM/Bi-LSTM networks were chosen for their ability to handle sequential data and long-term dependencies, making them ideal for tasks involving speech temporal characteristics. Alternative architectures such as WaveNet, Conv-TasNet, UNet, or VoiceFilter were considered but were deemed more suitable for tasks requiring finer temporal resolution or spectrogram-based processing.
Key Components
Input and Output
Input:
- Noisy audio clips containing speech mixed with various background noises.
- Audio length extended to 10 seconds for comprehensive analysis.

Output:
- Cleaned audio with minimized background noise and enhanced clarity of the speaker's voice.
Preprocessing Steps
1. Audio Data Collection:
- Collected audio samples containing speech in noisy environments (e.g., street noise, background music).

2. Conversion to Spectrogram:
- Applied Short-Time Fourier Transform (STFT) to convert raw audio into a spectrogram, representing frequency vs. time.
- This transformation aids in analyzing noise patterns and voice characteristics.

Why STFT? It enables the model to understand frequency variations over time, which is crucial for separating voice and noise.

3. Normalization:
- Normalized audio data to maintain consistent loudness across samples, aiding effective model training.

4. Data Augmentation:
- Used techniques such as pitch shifting and time stretching to increase dataset size and model robustness.
Model Architecture
1. LSTM (Long Short-Term Memory):
- LSTM layers were employed to process sequential audio data and capture long-term dependencies.
- These layers helped the model understand the temporal evolution of speech.

2. Bi-LSTM (Bidirectional LSTM):
- Added Bi-LSTM layers to process audio in both forward and backward directions.
- This architecture improved the model's ability to distinguish noise from speech by considering contextual relationships before and after a given point.
Post-Processing
1. Reconstruction with Inverse STFT:
- After filtering the spectrogram, inverse STFT was applied to convert the cleaned spectrogram back into a time-domain audio signal.
- This step generated the final cleaned audio output.
Evaluation Metrics
1. Signal-to-Distortion Ratio (SDR):
- Measured distortion reduction in the output audio compared to the noisy input. Higher SDR indicates cleaner output.

2. Signal-to-Noise Ratio (SNR):
- Compared the speech signal level to background noise. A higher SNR reflects better noise reduction.

3. PESQ (Perceptual Evaluation of Speech Quality):
- Quantified the resemblance of filtered audio to original clean speech based on human auditory perception.

4. STOI (Short-Time Objective Intelligibility):
- Evaluated speech intelligibility after filtering. Scores closer to 1 indicate clearer speech.
Results
1. Achieved significant improvements in SDR and SNR, demonstrating effective noise reduction and voice enhancement.
2. Extending the audio length to 10 seconds improved model performance on longer speech segments, ensuring accuracy in continuous speech scenarios.
Explanation Strategy for Interviews
1. Simplify Terminology:
- Use layman-friendly terms to explain complex concepts (e.g., 'transforming audio into an image-like representation' for spectrogram).

2. Highlight Key Contributions:
- Emphasize your role in data preprocessing, model selection, and achieving measurable improvements in audio quality.

3. Demonstrate Impact:
- Share tangible results (e.g., percentage improvements in SDR, SNR, or intelligibility metrics) to showcase the effectiveness of the solution.

