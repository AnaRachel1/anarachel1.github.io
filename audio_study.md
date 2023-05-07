# Understanding audio data

> **What is sound?**
> Sound is a vibration that propagates through an elastic medium and can be understood by hearing. 

Certain types of movements generate a change in the pressure of the environment in a way that produces a vibration of the molecules in alternating movements of condensation and rarefaction, which are the sound wave. When the medium is “elastic” like water and air, it is capable of undergoing these changes and then propagating sound.
A video that shows in a very interesting way how this vibration can be different according to the sound (its frequency) is linked [here](https://www.youtube.com/watch?v=wvJAgrUBF4w).

Therefore, sound waves in air are longitudinal mechanical waves that are formed by successive compressions and rarefactions of air (pressure variations). The equation that best represents the temporal variation of pressure at a point in the medium is described by a sigmoid function and the representation is called a waveform.

_**Sigmoid equation**: p (t) = p0 sin (wt)_
•	p(t): air pressure difference, for t moment; 
•	p0: inicial pressure,
•	w: angular frequency.

*Figura 1 – Air pressure zones* 
[Figura1](images/audio_basics/fig1_wave.jpg)
 
Os sons são caracterizados pela sua altura, intensidade e timbre. 
- **Altura**: A altura do som diz respeito à sua frequência. Sons altos são aqueles que apresentam grandes frequências, também chamados de sons agudos. Os sons baixos, por sua vez, são aqueles que apresentam baixas frequências, tratando-se, portanto, de sons graves.
- **Intensidade**: A intensidade do som diz respeito à quantidade de energia que a onda sonora transmite. Essa intensidade está relacionada à amplitude da onda sonora: quanto maior a sua amplitude, maior será sua intensidade. Medidos em decibel (dB).
- **Timbre**: O timbre do som é o que nos permite distinguir a natureza de sua fonte. Dois sons de mesma frequência e intensidade, mas que foram produzidos por instrumentos diferentes, podem ser diferenciados pelo timbre. Diz-se que o timbre é a cor do som.

### ADC: analog-digital converter
Digital recordings take that analog signal and convert it into a digital representation of the sound, which is essentially a series of numbers for digital software to interpret. To make this representation, it is necessary to discretize the continuous signal in time and magnitude.
- **Sample rate**: quantity of samples taken per second (Hz)
- **Bits depth**: amplitude or y discretization (bits)

_Note 1: a CD has SR of 44100 Hz and 16bits depth._
_Note 2: For Machine learning analysis, a SR of 22050Hz is sufficient._

*Figura 2 – Different bits depths representation* 
[Figura2](images/audio_basics/fig2_discretization.png)

## Sound representations
**Fourier Transform (FT)** breaks down a complex and periodic sound into waves that oscillate at different frequencies. It manages to find out which waves (of which frequencies) make up that sound. 

When applying Fourier, a **spectrum** representation of the sound is created. Then, it said that we had moved from the time domain to the frequency domain. In other words, we lost information about time!
 

A solution to be able to preserve time information and still have frequency information was to use **Short Time Fourier Transform (STFT)**. Basically, the Fourier transform is applied to each frame (which is a set of sound samples) in order to identify the frequencies at that moment and then apply again to the next frame and so on, several times throughout the song. Now, we have a **Spectrogram**!

 

Studies have shown that humans do not perceive frequencies on a linear scale. We are better at detecting differences in lower frequencies than in higher frequencies. So there is the Mel-scale that basically applies a logarithmic scale to the frequency, in order to a unit of pitch such that equal distances in pitch sounded equally distant to the listener.  The spectrogram in that scale is called **Mel-spectrogram**. 
Another representation very used in instrument/genre classification and speech recognition is the Mel Frequency Cepstral Coefficients (MFCCs). That is because it captures the timbre of that sound. To build the MFCCs, it is also necessary to use FT to get the frequency information but it also converts it to the perceptive way. 
_Note: in song analysis, it usually uses coefficients from 13 to 40._ 


> A git repository testing these concepts is in my [github] (https://github.com/AnaRachel1/Studying-audio-signals)
> See more there
 

### REFERENCES
**O que é som?**  Available in https://complexosonoro.com/2021/08/19/o-que-e-som-2/

**Audio Signal Pre-processing for machine learning**. Valerio Velardo. Available in https://www.youtube.com/watch?v=iCwMQJnKk2c&list=PL-wATfeyAMNqIee7cH3q1bh4QJFAaeNv0 

**Understanding the Mel Spectrogram**. Leland Roberts. https://medium.com/analytics-vidhya/understanding-the-mel-spectrogram-fca2afa2ce53
