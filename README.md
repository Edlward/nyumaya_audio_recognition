# Detect simple voice commands and audio events on small embedded sytems like the PiZero.
Classify audio with neural nets on embedded systems like the Raspberry Pi using Tensorflow. This should run on any Linux system fine, on other systems at least the recording implementation has to be changed.

To run the demo you have to download at least one of the models and provide the path to the label and graph file. Currently you can change the sensitivity in streaming_example.py. All models contain a result file wich describes the false positive/accuracy tradeoff. 

If you need a special combination of audio classes or model architecture trained create an issue and I will try to prioritize or train it.


To run an example

```
git clone --depth 1 https://github.com/nyumaya/nyumaya_audio_recognition.git
cd nyumaya_audio_recognition/python 
```
For Raspberry Pi 2/3
```
python streaming_example.py --libpath ../lib/rpi/armv7/libnyumaya.so
```
For Raspberry Pi Zero
```
python streaming_example.py --libpath ../lib/rpi/armv6/libnyumaya.so
```

For Linux
```
python streaming_example.py --libpath ../lib/linux/libnyumaya.so
```




The demo captures audio from the default microphone. The new version only takes .tflite models.
For each application, different model architectures are available which are a tradeoff between accuracy and cpu/mem usage.

## Model Architectures
- Small model  (CPU Pi0: 20% CPU Pi3 one core: 12%)
- Big model    (CPU Pi0: 95% CPU Pi3 one core: 20%)


## Applications:
- Speech_commands_subset (yes,no,up,down,left,right,on,off,stop,follow,play)
- Speech_commands_numbers (one,two,three,four,five,six,seven,eight,nine,zero)
- German_commands(an,aus,computer,ein,fernseher,garage,jalousie,licht,musik,oeffnen,radio,rollo,schließen,start,stopp)
- Marvin_hotword (marvin)
- Sheila_hotword (sheila)
- Voice-gender (female,male,nospeech)
- Baby-monitor (cry, babble, door-open, music, glass-break, footsteps, fire-alarm)
- Impulse-response (Play tone and interpret echo: Bedroom, Kitchen, Bathroom, Outdoor, Hall, Living Room, Basement)
- Alarm-system (door-open, glass-break, footsteps, fire-alarm, voice)
- Door-monitor (door bell, door knocking, voice)
- Weather (thunder, rain, storm, hail)
- Language detection
- Swear word detection (imagine some unappropriate words)
- Crowd monitoring(screaming, shouting, gunshot, siren, explosion)
- Animal monitoring (dog, cat, chicken, rooster..)

## Pretrained models:
- Marvin Hotword
- Sheila Hotword
- Command Subet
- Command Numbers


## Roadmap:
- [x] Basic working models
- [X] Average output predictions
- [X] Benchmark accuracy and false recognition rate
- [X] Noisy Benchmark, use more diverse test set (maby musan dataset)
- [ ] Improve Far Field Recognition
- [ ] Benchmark latency
- [ ] Voice activity detection
- [ ] Provide TensorflowLite and TensorflowJS models
- [ ] Web demo
- [ ] Improve Architectures (including RNN and Attention)
- [ ] More Applications 


## Credits:
- [https://github.com/castorini/honk](honk) For inspiration and model ideas
- Peter Warden for releasing the Speech Command Dataset
-  The library uses [https://github.com/mborgerding/kissfft](kissfft)

