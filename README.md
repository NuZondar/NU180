# NU180
A reverse-engineered replacement for the U180 hybrid in the Hewlett-Packard / Agilent / Keysight 3458A DVM. 

Briefly, the "U180" hybrid in the 3458A is prone to drifting or outright failure, but is absolutely unavailable. This project is a drop-in replacement for that hybrid. While not quite meeting every specification that a well-working U180 provides, it comes very close, reaching or exceeding 8 digit performance. 

Some notes:

The layout requires 6 layers. Choose a thin stackup - that is, thinner core layers - if available. That will provide better coupling to the internal ground planes. 

Choose the best resistors you can find, especially for their TCR (temperature coefficient of resistance). In particular, the use of low TCR bulk-foil resistors for at least the 50k and 80k's are suggested for best temperature stability. 

The footprints for the 50k and 80k's include overlaps, which will result in DRC errors or warnings. There is probably a better way to manage this, but it was deliberate and the errors are expected. The overlapping footprints allow choosing either standard 805 resistors, or large 2512 resistors, or else through-hole resistors. The standard resistor option is for people building boards on a budget or for testing purposes. The latter two options are intended for builders who are using bulk-foil resistors (80k's only come in 2512 size). You can edit the files to delete the unused footprints or else leave them in place. 

Another option for the 50k and 80k resistors is to edit the files to substitute a small array (there's room for up to 4 each) of series or parallel resistors, e.g. 4x 20k in series for the 80k, etc. 

You also have the option of using voltage regulation on the flip-flop and inverter (recommended), or else using unregulated 5V, chosen via jumpers. The schematic shows parts suitable for 3.3V operation, but other parts may allow operation down to 2.5V. The lower-voltage regulation should help keep noise down. 

The 100k resistors to ground are optional and need not be included unless some problem is seen. 

Note that builders have found some sensitivity to the values of the control line series resistors (the 100 Ohms ones in this design). When a NU180 equipped 3458A throws errors, sometimes changing those values up or down, e.g. to 33 or 220 Ohms, can help. Start with the four switch control lines associated with the 80k resistors. 

There is extensive discussion of this project in the metrology section of EEVblog. Many people contributed their knowledge and experience towards its success, including MiDi, DB4UCH, wanghar, Kleinstein and others. 

Good luck! 
