fftExtract - a general purpose audio spectrum feature extractor

Copyright (c) 2007-2014 Michael Casey, Dartmouth College
See LICENCE.txt

Usage
-----

fftExtract [options] inFile outFile

where options are:

-q B : constant-Q sepctrum B bands per octave (0=linear freq.)
-l L : low edge for CQ filter bank
-c C : chromagram folded into C bins
-n N : length of FFT
-w W : length of window within FFT
-h H : hop size
-b file : beat file for beat-synchronus features (secs)
-p file : fftw plan file (generates one if does not exist)
-v V : how much do you want to know? [0 - 10]

Examples:

16384 FFT, 8192 Win, 4410 hop
fftExtract -v 1 symphony5short.wav symphony5short.fft

2048 FFT, 1024 Win, 512 hop
fftExtract -v 1 -n 2048 -w 1024 -h 512 symphony5short.wav symphony5short.fft

12 bands per octave constant-Q transform using FFTW Plan file
fftExtract -v 1 -p fftwPlan.wis -q 12 symphony5short.wav foo.bin

24 bands per octave constant-Q transform with 8192 FFT
fftExtract -v 1 -n 8192 -p fftwPlan8192.wis -q 24 symphony5short.wav foo.bin

quiet 24 band chromagram, based on folded 24-band constant-Q spectrum
fftExtract -p fftwPlan.wis -c 24 symphony5short.wav foo.bin

OUTPUT:
output is binary matrix in following format

INT (vector size)
DOUBLE DOUBLE DOUBLE ... up to vector size
.
.
.
DOUBLE DOUBLE DOUBLE ... up to vector size
EOF

