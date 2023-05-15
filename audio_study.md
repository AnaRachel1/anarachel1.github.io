# **Understanding audio data**

> **What is sound?**
> Sound is a vibration that propagates through an elastic medium and can be understood by hearing. 

Certain types of movements generate changes in environment's pressure in a way that produces a vibration of the molecules, alternating between movements of condensation and rarefaction. That is the **sound wave**. When the medium is “elastic”, just like  water and air, it is capable of undergoing these changes and then propagating sound.

A video that shows in a very interesting way how this vibration can be different according to the sound (its frequency) is linked **[here](https://www.youtube.com/watch?v=wvJAgrUBF4w)**.

Therefore, sound waves in air are longitudinal mechanical waves that are formed by successive compressions and rarefactions of air (pressure variations). The equation that best represents the temporal variation of pressure at a point in the medium is described by a sigmoid function and the representation is called a waveform.

_Sigmoid equation: p (t) = p0 sin (wt)_

- p(t): air pressure difference, for t moment;  
- p0: inicial pressure,
- w: angular frequency.

*Figure 1 – Air pressure zones* 

<img src="images/audio_basics/fig1_wave.jpg" width="250" height="200"/>
 
Sounds are characterized by their pitch, intensity and timbre.
- **Pitch**: The pitch of the sound refers to its frequency. Loud sounds are those that have high frequencies, also called high-pitched sounds. Low sounds, in turn, are those that have low frequencies, therefore, they are serious sounds.
- **Intensity**: The intensity of the sound refers to the amount of energy that the sound wave transmits. This intensity is related to the amplitude of the sound wave: the greater its amplitude, the greater its intensity.
- **Timbre**: The timbre of the sound is what allows us to distinguish the nature of its source. Two sounds of the same frequency and intensity, but produced by different instruments, can be differentiated by timbre. It is said that timbre is the color of sound.

### ADC: analog-digital converter

For digital software to interpret a sound, we need to take a analog signal and convert it into a digital representation, which is essentially a series of numbers. To make this representation, it is necessary to discretize the continuous signal in time and magnitude.
- **Sample rate**: quantity of samples taken per second (Hz),
- **Bits depth**: amplitude or y discretization (bits).

_Note 1: a CD has SR of 44100 Hz and 16bits depth._
_Note 2: For Machine learning analysis, a SR of 22050Hz is sufficient._

*Figure 2 – The discretization of a continuous signal* 
<img src="images/audio_basics/fig2_discretization.png?raw=true" width="150" height="100"/>

## Sound representations

There is a mathematical model that is often used in audio analysis called **Fourier Transform (FT)**. This transformation breaks down a complex and periodic sound into waves that oscillate at different frequencies. In other words, it manages to find out which waves (at which frequencies) make up that sound. 

*Figure 3 – A complex sound* 
<img src="images/audio_basics/fig3_complex_sound.png?raw=true"/>

The waveform is the simplest sound representation in which we have information about time and amplitude. When applying Fourier to a waveform, we are able to see all the frequencies that sound is composed of, so a **spectrum** representation of the sound is created. In this case, it said that we had moved from the time domain to the frequency domain. In other words, we lost information about time!
 
*Figure 4 – The spectrum of a complex sound compost by two simple signals of 10 and 22 Hz* 
<img src="images\audio_basics\fig4_fourier.jpg?raw=true"/>

A solution to be able to preserve time information and still have frequency information is to use **Short Time Fourier Transform (STFT)**. Basically, the Fourier Transform is applied to each audio frame (which is a set of sound samples) in order to identify the frequencies at that moment and then apply again to the next frame and so on, several times throughout the song. Now, we have a **Spectrogram**!

*Figure 5 – Applying STFT* 
<img src="images\audio_basics\fig5_short_fourier.png?raw=true"/>

The famous **Mel-spectogram** is a Spectogram's adaptation. It turns out that peoples ears work on a logarithmic scale so that the ear can detect much finer changes in amplitude at low amplitudes than at high amplitudes. In order to get a better perception of amplitude, just like out ears would detect it, the amplitude is converted to decibels (dB) by applying _the Mel scale_ which is basically a logarithmic scale. The result of it is called Mel-Spectrogram!

Another representation very used in instrument/genre classification and speech recognition is the **Mel Frequency Cepstral Coefficients (MFCCs)**. That is because it captures the timbre of that sound. To build the MFCCs, it is also necessary to use FT to get the frequency information but it also converts it to the perceptive way. 

_Note: in song analysis, it usually uses coefficients from 13 to 40._ 

*Figure 6 – Mel-Spectrogram and MFFs* 
<img src="images\audio_basics\Fig6_ mfcc_mel.png?raw=true"/>


> A git repository testing these concepts is in my [github](https://github.com/AnaRachel1/Studying-audio-signals).
> <br> See more there.
 



### REFERENCES
**O que é som?**  Available in https://complexosonoro.com/2021/08/19/o-que-e-som-2/

**Audio Signal Pre-processing for machine learning**. Valerio Velardo. Available in https://www.youtube.com/watch?v=iCwMQJnKk2c&list=PL-wATfeyAMNqIee7cH3q1bh4QJFAaeNv0 

**Understanding the Mel Spectrogram**. Leland Roberts. https://medium.com/analytics-vidhya/understanding-the-mel-spectrogram-fca2afa2ce53
