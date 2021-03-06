# oscfile

The 'oscfile' project consists of two command line programs: 'oscrec' and 'oscplay'. As their names suggest, they record and playback Open Sound Control messages to and from files.

## command line usage

record messages from local port 3333 to file dump.osc

	oscrec -i osc://localhost:3333 -o dump.osc

record messages from local port 3333, compress them with xz and store them in file dump.osc.xz

	oscrec -i osc://localhost:3333 -o - | xz - > dump.osc.xz

playback messages stored in dump.osc to port 5555 on host 10.10.10.1 via tcp

	oscplay -i dump.osc -o osc.tcp://10.10.10.1:5555

playback xz compressed messages stored in dump.osc.xz to port 5555 on host 10.10.10.1 via tcp

	xzcat dump.osc.xz | oscplay -i - -o osc.tcp://10.10.10.1:5555

playback messages stored in dump.osc to local port 4444 with a delay of 3.1415926 seconds

	oscplay -d 3.1415926 -i dump.osc -o osc.udp://localhost:4444
