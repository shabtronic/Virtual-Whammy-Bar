# Virtual-Whammy-Bar
Virtual Whammy Bar for guitar


Here's the current status/plan:


Parts:

Daisy Seed CPU 480mz Arm-M7 with 96khz 24 bit audio in/out
https://www.electro-smith.com/daisy/daisy

RP2040 Cap Touch screen - use as the interface and whammy control. Use I2C comms
to the Daisy Seed to control the pitch shifter. Needs firmware written for the comms
and display e.t.c. should be simple enough. RP2040 has LI-ON charge circuit - so RP2040 can power the Daisy Seed. 
RP2040 on the front of the Guitar near the Volume controls for easy finger access. Daisy Seed on the strap or edge with battery for power.
https://www.amazon.co.uk/dp/B0C4YV9HRX

Input Buffer: (needed to convert guitar Hi-Z to Lo-Z for the Daisy Seed input)

	2x 1m resistor
 
	10uf electrolytic cap
 
	100nf film/poly cap
 
	LM741CN opamp
 
 	<https://github.com/shabtronic/Virtual-Whammy-Bar/blob/main/BufferCircuit.png>
 
Total Cost:

	Daisy Seed £30
 
	RP2040 Touch £30
 
	Buffer parts £10
 
	£70 incl Vat+Shipping


Software:

	RP2040 Continually sends Touch Down and Position via I2C to the daisy seed.
	Daisy seed interprets that data and does whatever: Change pitch, 
 	change operating mode e.t.c. RP2040 has automatic gesture 
  	recognition - could be handy for other stuff.

  
	Input Audio
 
		Format Removal
  
		Pitch shift
  
		Formant Reapplication
  
	Output Audio
	
Research Needed:
	
	Software Platform: Native Daisy Seed or Daisy Arduino
  	Arduino has been tested - it's ok - no hardware SPI - but that's not needed
   	in this project - so it's the preferred platform.

  	RP2040 programming not tested in Arduino yet - to do! 
   	Native RP2040 is a bit of a pain to setup.
		 
	best pitch shift algo
		Naive ring buffer
		FFT
		Other?
		Daisy Seed already has a pitch shift algo - not tested probably a crappy ring buffer thing.  		
    		<https://github.com/breakfastquay/rubberband>   		
      		<https://github.com/Collaboarator/ShortTimeFourierPitchShifterJS>		
		<https://www.ee.columbia.edu/~dpwe/papers/LaroD99-pvoc.pdf>
  		<https://www.youtube.com/watch?v=fJUmmcGKZMI>
    		<https://www.guitarpitchshifter.com/>
	
 	power consumption and battery?
		unknown? 250ma@5v?
		9v PP3 or 4.2v Li-on
			will the input buffer work at 4.2v?

Operating Modes:

	Quantised - touch circle is split into segments for semitone shifting. Will bend up or down 
 	and at variable speed depending on segment movement speed:
 	Smoothed Raw - touch circle bends notes based on arc position from initial touch down point.
  	Vibrato: Amount controlled by distance from center of touch circle.
  	Maybe have notches on outer part of display for tactile feedback.

Possible Issues:

RP2040 near pickups may cause interference on high/low gain - investigate this.

Status:
		
Currently working on a Multi-band Naive pitch shifter algo experiment whilst I wait for the buffer 
components to arrive!
