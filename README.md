# CountPaTaKa

This task is based on ALICE to produce PaTaKa detection<br>
See the [Automatic LInguistic Unit Count Estimator (ALICE)](https://github.com/orasanen/ALICE) for the reference

## Requirements

ALICE has been developed and so-far tested for a range of Linux and macOS environments.

Packages:

- Conda (https://docs.conda.io/en/latest/)
- CMake (```pip install cmake``` or ```conda install cmake```)
- Sox (http://sox.sourceforge.net/ , ```brew install sox``` (macOS with Homebrew installed), ```sudo apt-get install sox```(Ubuntu))

(other packages are automatically installed by conda environment)

# Installation 

- Clone the repository with submodules :

```bash
git clone --recurse-submodules https://github.com/orasanen/ALICE/
```

- Make sure you have Conda, Cmake and Sox installed.

- Create the conda environment installing all the dependencies. Note that this is OS dependent:

```bash
cd ALICE
```  

On Linux:  
```
conda env create -f ALICE_Linux.yml 
```

On macOS:  
```  
conda env create -f ALICE_macOS.yml 
```

## Usage

Always activate the ALICE conda environment before usage. To do this, run:
```
  $ conda activate ALICE
```

Since ALICE need 16khz sampling rate and ptk_2.wav has a sampling rate of 44100. 

I convert ptk_2.wav audio files to 16kHz before using the ALICE.

To process .wav files containing the audio of interest, run:
```
  $ ./run_ALICE.sh ptk_2_2.wav
```
  where <data_location> = folder of .wavs, path to a .wav, or path to a .txt file
  with a list of .wav paths, one per row.

  For GPU use during diarization , use
```
  $ ./run_ALICE.sh ptk_2_2.wav gpu
```

## Result

Open ALICE_output.txt

```
FileID 	 phonemes 	 syllables 	 words
ptk_2_2	182	94	60
```

You can use ALICE read 94 syllables.

Pa , Ta and Ka each word represent one syllables.

if we need to the entire phrase “Pa Ta Ka” as one unit.

the result should be 94/3=31 times (Pa Ta Ka) for the .wav files
