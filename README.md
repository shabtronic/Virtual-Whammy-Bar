# Virtual-Whammy-Bar
Virtual Whammy Bar for guitar


Here's the current status/plan:


Parts:

Daisy Seed CPU 480mz Arm-M7 with 96khz 24 bit audio in/out
https://www.electro-smith.com/daisy/daisy

OLED Screen or Tri color LED

Rotary encoder + metal pitch wheel (for capacitive touch)

Any buttons,switches or jacks

Input Buffer: (needed to convert guitar Hi-Z to Lo-Z for the Daisy Seed input)
	2x 1m resistor
	10uf electrolytic cap
	100nf film/poly cap
	LM741CN opamp
 https://github.com/shabtronic/Virtual-Whammy-Bar/blob/main/BufferCircuit.png

Software:

	Read Pitch Wheel
 
		Is metal wheel touched?
  
		read rotary encoder relative to where it was first touched
  
	Input Audio
 
		Format Removal
  
		Pitch shift
  
		Formant Reapplication
  
	Output Audio
	
Research Needed:
	
	Software Platform
		Native Daisy Seed or Arduino
	
	OLED Screen, LED Segement display or TriColour LED
	
	best rotary encoder
		Current Fav for size/resolution and small amount of cpu connections
			 https://uk.rs-online.com/web/p/mechanical-rotary-encoders/7377697
			 
	best pitch shift algo
		Naive ring buffer
		FFT
		Other?
		Daisy Seed already has a pitch shift algo - not tested probably a crappy ring buffer thing.
  		https://github.com/breakfastquay/rubberband
    		https://github.com/Collaboarator/ShortTimeFourierPitchShifterJS
	
	power consumption and battery?
		unknown? 250ma@5v?
		9v PP3 or 4.2v Li-on
			will the input buffer work at 4.2v?


Status:
		
Currently working on a Multi-band Naive pitch shifter algo experiment whilst I wait for the buffer 
components to arrive!
