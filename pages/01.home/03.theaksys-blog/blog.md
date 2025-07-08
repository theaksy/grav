# Trialling the SDRPlay RDPdx
I managed to borrow an [SDRPlay SDRdx](https://www.sdrplay.com/rspdx/) which  has better [specs](https://www.sdrplay.com/resources/RSPdxDatasheet.pdf) to the RTL SDR v4 and HackRF One. In particular I was interested in the larger 14-bit ADC that may help me with the NOAA reception so close to an FM transmitter.

# Software
After plugging in I couldnt see it in SatDump as a source, though the docs say it is supported. Therefore I downloaded [SDR Connect](https://www.sdrplay.com/sdrconnect/) 

During the installation it mentioned installing soem drivers for the SRDPlay so this looked promising. Within Device Manager the SDRplay RSPdx was showing under Software Defined Radio. Folowing a restart of SatDump I still couldn't see it as a source, however I opened SDRconnect and it could successfully connect to the receiver.

It seems SatDump uses the sdrplay_api.dll to interface, this file is in my Satdump directory. I installed the [SDRPlay API](https://www.sdrplay.com/api/) and could se the SDRplayAPIService running in TaskManager/Services.

Following a restart of SatDump the receiver was available and streaming ok. THe likelihood is I just needed the API installing.
