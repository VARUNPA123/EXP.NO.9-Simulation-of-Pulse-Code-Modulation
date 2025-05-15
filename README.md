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
    import matplotlib.pyplot as plt
    import numpy as np
    
    # Parameters
    sampling_rate = 5000
    duration = 0.1
    quantization_levels = 16
    
    # Time base
    t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)
    
    # Two message signals
    frequency1 = 50
    frequency2 = 100
    message_signal1 = np.sin(2 * np.pi * frequency1 * t)
    message_signal2 = np.sin(2 * np.pi * frequency2 * t)
    
    # Quantization
    def quantize(signal, levels):
      step = (max(signal) - min(signal)) / levels
      quantized = np.round(signal / step) * step
      pcm = ((quantized - min(quantized)) / step).astype(int)
      return quantized, pcm
    
    quantized_signal1, pcm_signal1 = quantize(message_signal1, quantization_levels)
    quantized_signal2, pcm_signal2 = quantize(message_signal2, quantization_levels)
    
    # Multiplexing the PCM signals
    # Interleaving samples from both signals
    multiplexed_pcm = np.empty((pcm_signal1.size + pcm_signal2.size,), dtype=int)
    multiplexed_pcm[0::2] = pcm_signal1
    multiplexed_pcm[1::2] = pcm_signal2
    
    # Time base for multiplexed stream (double samples)
    t_mux = np.linspace(0, duration, multiplexed_pcm.size, endpoint=False)
    
    # Clock signal for reference
    clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))
    
    # Plotting
    plt.figure(figsize=(12, 10))
    
    plt.subplot(8, 1, 1)
    plt.plot(t, message_signal1, label="Message Signal 1 (50Hz)", color='black')
    plt.title("Original Message Signal 1")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)
    plt.legend()
    
    plt.subplot(8, 1, 2)
    plt.plot(t, clock_signal, label="Clock Signal", color='blue')
    plt.title("Clock Signal")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)
    
    plt.subplot(8, 1, 3)
    plt.step(t, quantized_signal1, label="Quantized Signal 1", color='red')
    plt.title("Quantized Signals")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)
    plt.legend()
    
    plt.subplot(8, 1, 4)
    plt.plot(t, message_signal2, label="Message Signal 2 (120Hz)", color='orange', alpha=0.7)
    plt.title("Original Message Signal 2")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)
    plt.legend()
    
    plt.subplot(8, 1, 5)
    plt.plot(t, clock_signal, label="Clock Signal", color='red')
    plt.title("Clock Signal")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)
    
    plt.subplot(8, 1, 6)
    plt.step(t, quantized_signal2, label="Quantized Signal 2", color='purple', alpha=0.7)
    plt.title("Quantized Signals")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)
    plt.legend()
    
    plt.subplot(8, 1, 7)
    plt.step(t, quantized_signal1, label="Quantized Signal 1", color='green')
    plt.step(t, quantized_signal2, label="Quantized Signal 2", color='purple', alpha=0.7)
    plt.title("Quantized Signals")
    plt.xlabel("Time [s]")
    plt.ylabel("Amplitude")
    plt.grid(True)
    plt.legend()
    
    plt.subplot(8, 1, 8)
    plt.step(t_mux, multiplexed_pcm, label="Multiplexed PCM Signal", color='brown')
    plt.title("Multiplexed PCM Signal (Interleaved)")
    plt.xlabel("Time [s]")
    plt.ylabel("PCM Value")
    plt.grid(True)
    plt.legend()
    
    plt.tight_layout()
    plt.show()

# OUTPUT
![image](https://github.com/user-attachments/assets/321b7cca-4005-42b8-9c14-8225dbed0140)


# RESULT / CONCLUSIONS
Thus, the simulation of Pulse Code Modulation is carried out successfully using Python and the output waveform is observed. 
