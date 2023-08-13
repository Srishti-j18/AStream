AStream: A rate adaptation model for DASH
==================
AStream is a Python based emulated video player to evalutae the perfomance of the DASH bitrate adaptaion algorithms.


Rate Adaptatation Algorithms Supported
--------------------------------------
1. Basic Adaptation
2. Segment Aware Rate Adaptation (SARA): Our algorithm
3. Buffer-Based Rate Adaptation (Netflix): This is based on the algorithm presented in the paper. 
   Te-Yuan Huang, Ramesh Johari, Nick McKeown, Matthew Trunnell, and Mark Watson. 2014. A buffer-based approach to rate adaptation: evidence from a large video streaming service. In Proceedings of the 2014 ACM conference on SIGCOMM (SIGCOMM '14). ACM, New York, NY, USA, 187-198. DOI=10.1145/2619239.2626296 http://doi.acm.org/10.1145/2619239.2626296

Logs
----

Buffer Logs:

1. Epoch time
2. Current Playback Time
3. Current Buffer Size (in segments)
4. Current Playback State

Playback Logs:

1. Epoch time
2. Playback time
3. Segment Number
4. Segment Size
5. Playback Bitrate 
6. Segment Size 
7. Segment Duration
8. Weighted harmonic mean average download rate



The AStream DASH video client is compatible with both Python 2 and Python 3. Therefore, please follow the instructions below before running the DASH client code.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

#### Option1 (Python3):
If you prefer to use Python3 as Python 3 is faster, and its syntax is more user-friendly,We must install Python3 to run the DASH video client, and we will also install the video encoding utility `ffmpeg` so that we can reconstruct the video later:
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```bash
sudo apt update
sudo apt install -y python3 ffmpeg
```

#### Option2 (Python2):
Alternatively, If anyone would like to use Python2 for the experiments, follow these instructions:

Install Python 2 and the video encoding utility ffmpeg:
-------------------------------------------------------
```
sudo apt update
sudo apt install -y python2 ffmpeg
```

Next, install pip for Python 2 and install the required six library:
--------------------------------------------------------------------
```
sudo apt update
wget https://bootstrap.pypa.io/pip/2.7/get-pip.py
sudo python2 get-pip.py
pip2 install six
```


Sample Run
----------
```
python dist/client/dash_client.py -m <URL TO MPD> -p <PlaybackType> 
```

Command Line options
--------------------
```
dash_client.py [-h] [-m MPD] [-l] [-p PLAYBACK] [-n SEGMENT_LIMIT] [-d]

Process Client parameters

optional arguments:
  -h, --help            show this help message and exit
  -m MPD, --MPD MPD     Url to the MPD File
  -l, --LIST            List all the representations and quit
  -p PLAYBACK, --PLAYBACK PLAYBACK
                        Playback type ('basic', 'sara', 'netflix', or 'all')
  -n SEGMENT_LIMIT, --SEGMENT_LIMIT SEGMENT_LIMIT
                        The Segment number limit
  -d, --DOWNLOAD        Keep the video files after playback
```
