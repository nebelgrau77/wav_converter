```python

import scipy.io.wavfile as wavfile
import librosa

def wave_converter(filename, resampled_sr=16000, prefix="resampled_", mix2mono = False):

    '''
    Resample WAV soundfile to a different sample rate.
    
        Input: original sound file
        Output: resampled sound file
        Parameters: 
            - name of the file to be converted, 
            - destination sample rate, default = 16kHz
            - prefix to identify resampled files
            - mix to mono channel, default = False (leave as-is)
            
        Notes: for simplicity it needs to be run in the folder with the files we are converting
    '''    
    
    resampled_file = prefix + filename 
    origin_sr, origin_data = wavfile.read(filename)
    origin_type = origin_data.dtype
    
    resampled_data = librosa.resample(origin_data.T.astype('float'), origin_sr, resampled_sr) # transpose array to librosa shape
    if mix2mono == True:
        resampled_data = librosa.to_mono(resampled_data)        
    resampled_data = resampled_data.T.astype(origin_type) # transpose back to scipy.io.wavfile shape
    
    wavfile.write(resampled_file, resampled_sr, resampled_data)
    
    print('Resampled wavefile saved to {}'.format(resampled_file))

```
