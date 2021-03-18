This project is an attempt to restore XXDP sources

XXDPP.MAC              - The restored source of the XXDP+ monitor and the MACRO listing file.
XXDPP.LST              - The listing file
XXDPP.PDF              - Listing file PDF

XXDP V2 Driver Guide   - Transcription of the V2 driver guide, minus the appendices.
XXDP V2 User Guide     - Original
XXDP+ File Structure   - Transcription
XXDP+ Programming Card - Original
XXDP+ Help File        - Orginal

Source introduction:

XXDP was/is the diagnostic operating system for PDP-11 computers.
This source file was created by reverse assembling the binary image
of the XXDP+ HMDLD0 monitor found on XXDP23 distribution.

XXDP constitutes the de factor definition of the PDP-11, as anyone
who writes an emulator soon finds out. It's the toughest the PDP-11
systems, case-hardened by its use on only partially functioning 
systems.

XXDP's architecture is based on a simple, near-boolean level state
machine. There is rarely any analytic vagueness regarding system 
state.

XXDP has a remarkably flat structure. Registers rarely need to be
saved/restored across routines (less than 10 instances). All
parameters and results are passed in registers, obeying a strict
usage protocol.

Because of the fixed space restrictions placed on the monitor, code
compression was always required to find space for new functionality.
XXDP uses many software techniques to achieve that goal. The code 
is heavily compressed.

One overarching simplification is the almost complete absence of
sanity testing. It will accept any disk volume as an XXDP volume, 
no matter how crazy the directory structure might appear. It tests
only for conditions that make it impossible to continue.

The original XXDP+ would of course have had separate source modules
for the monitor and the various drivers. For this stage of the
recovery process I've thought it best to have everything in a single
source module with no external dependencies.

The monitor source code translation is complete with this release.
However, the documentation requires a programmer's guide and a system
logic manual, at some distant point in time. For clarity I have not
used macro definitions for system EMT calls in this, preferring to
see all the binary code instructions. A later release should employ
macros for system calls. The comments can also be improved.

The XXDP monitor itself is restricted to read-only support for system
media. The other half of the system, that creates and writes files,
is buried in a DRVCOM package that are embedded in the UPD1, UPD2, 
PATCH and XTECO utilities and the stand-alone drivers.

I began looking at XXDP around year 2000 when I used it to test a
PDP-11 emulator I'd written. I got curious and wrote a simple
disassembler and began annotating it (which I came back to in 2010
and 2015). At first I approached the project as an act of diligence:
I thought the source was important for the history of the PDP-11. 
However, it turned out to be a fascinating task and it was a real 
joy to see the operating system as a whole slowly emerge. There were
so many subtleties to be discovered. There's some horrible HELLO 
WORLD coding here and there, but most of it is tight and the state 
machine design is highly disciplined.

Some grateful acknowledgements:

I spent so much time in Al Kossow's amazing bitsavers.org that I 
thought I should start paying rent. I crawled endlessly through
diagnostics, looking for tiny clues. Joerg Hoppe's extensive XXDP
microfiche contributions to bitsavers included some critical sources.
A sometime DEC diagnostic programmer, Michael Moroney, who visited 
alt.sys.pdp11 some years ago, was kind enough to dig up and send me	
a copy of MACROM.MAC, the XXDP+ system macro module, which was truly 
invaluable: I had "names" for the system services. There have been
quite a few valuable websites that have dedicated time and space to
XXDP over the years from which I have gleaned information.
