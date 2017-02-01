---
layout: page
title: Specification > MultiMedia
header: Pages
---
{% include JB/setup %}


## Summary

The MultiMediaSessions message supports multimedia streaming with metric information including number of coded session streams, codec name for individual session stream. The body section of the MultiMedia
data consists of two parts: multimedia header to transfer the metric information and session streams from the codecs.
The MultiMediaSDP message wraps the Session Initiation Protocol(SIP) and Session Description Protocol(SDP).

## Message Types
### MultiMediaSessions
The Multimedia session message supports concatenation of several session streams. A session stream normally contains the payload descriptor, payload header and the bitstream, though the session stream structure might vary depending on the codec. Multimedia session message wrappes the session streams and handles the socket communication among servers and clients. This might deteriorate the performance the codecs, as some codecs have their own RTP packet management, for example, H264 and H265 could aggregation several small NAL unit into a single RTP packet.
<table border="1" cellpadding="5" cellspacing="0" align="center">
<tr>
<td style="background:#e0e0e0;"> Data
</td><td style="background:#e0e0e0;"> Type
</td><td style="background:#e0e0e0;"> Description
</td></tr>
<tr>
<td align="left"> Version
</td><td align="left"> 16bit unsigned short
</td><td align="left"> version number
</td></tr>
<tr>
<td align="left"> NSessionStreams
</td><td align="left"> 8bit unsigned short
</td><td align="left"> total number of session stream
</td></tr>
<tr>
<td align="left"> CodecName1
</td><td align="left"> char[30]
</td><td align="left"> the codec of the session stream
</td></tr>
<tr>
<tr>
<td align="left"> SessionName1
</td><td align="left"> char[30]
</td><td align="left"> the session name, as multiple sessions using the same codec might be sent
</td></tr>
<tr>
<td align="left"> SessionStreamLength1
</td><td align="left"> 32bit unsigned int
</td><td align="left"> the length of the session stream in bytes
</td></tr>
<tr>
<td align="left"> CodecName2
</td><td align="left"> char[30]
</td><td align="left"> the codec of the session stream
</td></tr>
<tr>
<tr>
<td align="left"> SessionName2
</td><td align="left"> char[30]
</td><td align="left"> the Session name of the session stream, as multiple 
</td></tr>
<tr>
<td align="left"> SessionStreamLength2
</td><td align="left"> 32bit unsigned int
</td><td align="left"> the length of the session stream in bytes
</td></tr>
<tr>
<td align="left"> SessionStream1
</td><td align="left"> Binary data 
</td><td align="left"> Individual session stream
</td></tr>
<tr>
<td align="left"> SessionStream2
</td><td align="left"> Binary data 
</td><td align="left"> Individual session stream
</td></tr>
</table>
### MultiMediaSDP 
This message wraps the Offer/Answer Model Session Description Protocol(SDP), which is commonly used in codecs to setup initial communication, exchange parameter settings of the codecs.

<table border="1" cellpadding="5" cellspacing="0" align="center">
<tr>
<td style="background:#e0e0e0;"> Data
</td><td style="background:#e0e0e0;"> Type
</td><td style="background:#e0e0e0;"> Description
</td></tr>
<tr>
<td align="left"> Version
</td><td align="left"> 16bit unsigned short
</td><td align="left"> version number
</td></tr>
<tr>
<td align="left"> SessionProtocolType
</td><td align="left"> 8bit unsigned short
</td><td align="left"> specify the protocol type, currently only SIP and SDP.
</td></tr>
<tr>
<td align="left"> SessionProtocol
</td><td align="left"> text data
</td><td align="left"> protocol text.
</td></tr>
</table>

## Implementations

## Contributors
* Longquan Chen, Junichi Tokuda
