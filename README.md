### WAV converter
Convert WAV files to a selected sample rate and/or mix down to mono. Useful for batch processing WAV files, e.g. for machine learning purposes.
Can convert to a given sample rate, optionally mix down to mono, preserves the bit resolution.

#### Usage: 
It is intended to run in a Jupyter notebook/IPython session, it is not a stand-alone script.

#### Notes:
For simplicity it DOES NOT handle file system paths, it will not work correctly with a whole path. Therefore it must be wav_converter('myfile.wav')
and not wav_converter('my_files/my_file.wav')
