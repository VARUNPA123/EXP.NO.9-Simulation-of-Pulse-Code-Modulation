# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

# AIM
To simulate Pulse Code Modulation which converts an analog input signal into digital data by sampling, quantizing and encoding.
# SOFTWARE REQUIRED
Google Colab

# ALGORITHMS
1. **Define parameters**: Set the sampling rate, message signal frequency, duration, and quantization levels.  
2. **Generate time vector**: Create a time sequence for the defined duration and sampling rate.  
3. **Create message signal**: Generate a sine wave signal with the specified frequency.  
4. **Generate clock signal**: Construct a sampling clock signal with a frequency of 200 Hz using a sine wave.  
5. **Quantize message signal**: Compute the quantization step size and round the message signal to the nearest quantized value.  
6. **Simulate PCM signal**: Normalize the quantized signal and convert it into integer values for digital representation.  
7. **Plot signals**: Visualize the message signal, clock signal, quantized PCM signal, and demodulated signal.

# PROGRAM
    import numpy as np
    import matplotlib.pyplot as plt
    
    # Parameters
    sampling_rate = 5000  # Sampling rate (samples per second)
    frequency = 50  # Frequency of the message signal (analog signal)
    duration = 0.1  # Duration of the signal in seconds
    quantization_levels = 16  # Number of quantization levels (PCM resolution)

    # Generate time vector
    t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

    # Generate message signal (analog signal)
    message_signal1 = np.sin(2 * np.pi * frequency1 * t)
    message_signal2 = np.sin(2 * np.pi * frequency2 * t)

    # Generate clock signal (sampling clock) with higher frequency than before
    clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))  # Increased clock frequency to 200 Hz

    # Time-Division Multiplexing (TDM): Interleave both signals
    multiplexed_signal = np.zeros_like(t)

    # Quantize the message signal
    quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels
    quantized_signal = np.round(message_signal / quantization_step) * quantization_step

    # Simulate the PCM modulated signal (digital representation)
    pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step
    pcm_signal = pcm_signal.astype(int)

    # Plotting the results
    plt.figure(figsize=(12, 10))

    # Message signal
    plt.subplot(4, 1, 1)
    plt.plot(t, message_signal, label="Message Signal", color='blue')
    plt.title("Message Signal")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)

    # Clock signal (higher frequency)
    plt.subplot(4, 1, 2)
    plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='brown')
    plt.title("Clock Signal (Increased Frequency)")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)

    # PCM modulated signal (quantized)
    plt.subplot(4, 1, 3)
    plt.step(t, quantized_signal, label="PCM Modulated Signal", color='green')
    plt.title("PCM Modulated Signal (Quantized)")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)

    # PCM Demodulation
    plt.subplot(4, 1, 4)
    plt.plot(t, quantized_signal, label="Signal Demodulation", color='red', linestyle='--')
    plt.title("Signal Without Demodulation")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)

    plt.tight_layout()
    plt.show()

# OUTPUT
![image](https://github.com/user-attachments/assets/7282069e-0354-49f4-a322-2ff8e70f094e)

# RESULT / CONCLUSIONS
Thus, the simulation of Pulse Code Modulation is carried out successfully using Python and the output waveform is observed. 
