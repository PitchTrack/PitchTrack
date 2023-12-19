# PitchTrack   

For pitch estimation, there are many related algorithms, mainly based on frequency domain processing or autocorrelation processing. We have conducted numerous evaluations and comparisons using the following algorithms:  

- **`PEF`** - Pitch Estimation Filter. A pitch estimation filter is designed, and pitch is estimated by performing cross-correlation operations in the frequency domain. [1]  
- **`NCF`** - Normalized Correlation Function. Pitch is estimated using normalized time-domain autocorrelation. [2]   
- **`HPS`** - Dot-Harmonic Spectrum. Pitch is estimated by adopting dot operations on the harmonics of the spectrum. [3]    
- **`LHS`** - Log-Harmonic Summation. Pitch is estimated by adopting sum operations on the harmonics of the spectrum. [4]     
- **`CEP`** - Cepstrum Pitch Determination. Pitch is estimated by performing a second FFT transformation on the spectrum and using cepstral analysis. [5]   
- **`YIN`** - Pitch is estimated using time-domain differential autocorrelation. [6]

The online experience for instrument pitch track based on web audio and wasm, [See the site here](https://aifasttune.com)   

### Build 
The library is cross-platform and currently supports Linux, macOS, Windows, iOS, Android and WebAssembly. 

For macOS example, enter project **scripts** directory and switch to the current directory, run the following script to build and compile: 

```bash
$ ./build_macOS.sh  
```  
> Before building, make sure the required compilation environment for the current system is available, such as Xcode for iOS/macOS, NDK for Android, emcc for WebAssembly, etc.


### Use
Quickstart, the python command line tools:   

```bash 
$ pitch -p pef -r 32000 -i test.wav -o test.txt

```
> `-p`, `--pitch`,  select pitch detection algorithm, include `pef`|`ncf`|`hps`|`lhs`|`cep`|`yin`  
> `-r`, `--samplate`, select samplerate   
> `-h`, `--help`, all parameter information  

Considering the characteristics of the above algorithms, for low-frequency pitch estimation of musical instruments (below 55Hz), most algorithms, except HPS/LHS, are ineffective. However, HPS/LHS performs relatively poorly in high-frequency pitch estimation (above 1000Hz). All algorithms face challenges of strong resonant peak interference and misjudgments. PEF shows better performance in handling pitch-related resonant peaks. In scenarios with slightly stronger background noise, the latency of all algorithms rapidly increases. 

<p align="center">
  <a target="_blank" href="https://aifasttune.com"><img alt="open in online experience" src="https://img.shields.io/badge/Open%20In%20Online%20Tuner-blue?logo=js&style=for-the-badge&logoColor=green"></a>
</p>

<p align="center">
  	 <img src='./image/fasttune.gif'  style="width: 600px;" >
</p>


### References
  
[1] Gonzalez, Sira, and Mike Brookes. "A Pitch Estimation Filter robust to high levels of noise (PEFAC)." 19th European Signal Processing Conference. Barcelona, 2011, pp. 451–455.  

[2] Atal, B.S. "Automatic Speaker Recognition Based on Pitch Contours." The Journal of the Acoustical Society of America. Vol. 52, No. 6B, 1972, pp. 1687–1697.  

[3] Tamara Smyth. "Music270a: Signal Analysis." 2019, Department of Music, University of California.   

[4] Hermes, Dik J. "Measurement of Pitch by Subharmonic Summation." The Journal of the Acoustical Society of America. Vol. 83, No. 1, 1988, pp. 257–264. 

[5] Noll, Michael A. "Cepstrum Pitch Determination." The Journal of the Acoustical Society of America. Vol. 31, No. 2, 1967, pp. 293–309.   

[6] Alain de Cheveigne, Hideki Kawahara. "YIN, a fundamental frequency estimator for speech and music." 2002 Acoustical Societyof America. 

