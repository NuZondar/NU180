# NU180
A reverse-engineered replacement for the U180 hybrid in the Hewlett-Packard / Agilent / Keysight 3458A DVM. 

Briefly, the custom "U180" hybrid in the 3458A is infamously prone to excessive drifting or outright failure, but is absolutely unavailable. NU180 is a drop-in replacement for that hybrid. Still under development, its performance falls slightly short of an original U180, e.g. noise performance is ~20-30% higher, but it thus provides at least 8 digits conversion (within 2x of 8.5 digits), which is infinitely better than a dead or dying machine! 

Some notes:

The layout requires 6 layers. Choose a thin stackup - that is, thinner core layers - if available. That will provide better coupling to the internal ground planes. 

Choose the best resistors you can find, especially for their TCR (temperature coefficient of resistance). In particular, the use of low TCR bulk-foil resistors for at least the 50k and most-critical 80k's are recommended for best temperature stability. 

The footprints for the critical 50k and 80k's include overlaps, which will result in DRC errors or warnings. There is probably a better way to manage this, but this was deliberate and the errors are expected. The overlapping footprints allow choosing either standard 805 resistors, or large 2512 resistors, or else through-hole resistors. The standard resistor option is for people building boards on a budget or for testing purposes. The latter two options are intended for builders who are using bulk-foil resistors (80k's only come in 2512 size). You can edit the files to delete the unused footprints or else leave them in place. 

Another option for the 50k and 80k resistors is to edit the files to substitute a small array of series or parallel resistors. There's room for up to 4 each, e.g. 4x 20k in series for the 80k's, etc. 

You also have the option of using voltage regulation on the flip-flop and inverter (recommended), or else using unregulated 5V, chosen via jumpers. The schematic shows parts suitable for 3.3V operation, but other parts may allow operation down to 2.5V. The lower-voltage regulation should help keep noise down. 

The 100k resistors to ground are optional and need not be included unless some problem is seen. 

Debugging: The 3458A is a very sensitive instrument that can be quite fussy about error codes. At least in earlier versions, builders have sometimes found that changing the value of the series resistors (the 100 Ohm ones) up or down, e.g. to 33 or 220 Ohms, can help. Usually, only the four switch control lines associated with the 80k resistors (S5, S7, S9, S11) might need tuning. Another hack that has sometimes helped is adding a small capacitor (5-10 pF) in parallel with the R140 resistor on the A3 board.

There is extensive discussion of this project in the metrology section of EEVblog. Many people contributed their knowledge and experience towards its success, including MiDi, DB4UCH, wanghar, Kleinstein and others. 

Good luck! 
