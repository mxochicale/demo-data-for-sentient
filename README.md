# Demo data for sentient 
This repo contains demo data for [S.E.N.T.I.E.N.T.](https://github.com/mxochicale/sentient) library (Sensor Enhanced Network Technology Integrating Evolving Neural Tools). 

## Surgical-skill-assessment data
### Intro
Demo data for surgical-skill-assessment look like this:
```
├── [5.9M]  p01t01r01-60ss.mp4
├── [1.4M]  p01t01r01-60ss.mp4.csv
├── [8.3M]  p01t02r01-60ss.mp4
├── [1.5M]  p01t02r01-60ss.mp4.csv
├── [6.8M]  p01t03r01-60ss.mp4
└── [1.5M]  p01t03r01-60ss.mp4.csv
```
See further details [here](https://github.com/mxochicale/sentient/tree/main/data/surgical-skill-assessment).    
The whole demo datasets (1.3 GB) can be downloaded from zenodo: https://doi.org/10.5281/zenodo.10775099.    
Notes. you can host up to 50GB of data in zenodo.

### Creating demo data
```
# creating 60seconds vidoes
ffmpeg -i participant01-test01-rep01-1g-5mins.avi -ss 00:00:00 -to 00:01:00 -c:v copy -c:a copy p01t01r01-60s.mp4
ffmpeg -i participant01-test02-rep01-1g-5mins.avi -ss 00:00:00 -to 00:01:00 -c:v copy -c:a copy p01t02r01-60s.mp4
ffmpeg -i participant01-test03-rep01-1g-5mins.avi -ss 00:00:00 -to 00:01:00 -c:v copy -c:a copy p01t03r01-60s.mp4

# create frame labels in the video
ffmpeg -i p01t01r01-60s.mp4 -vf "drawtext=fontfile=Arial.ttf: text=%{n}: x=0: y=h-th: fontcolor=white: box=1: boxcolor=0x00000099" p01t01r01-60ss.mp4
ffmpeg -i p01t02r01-60s.mp4 -vf "drawtext=fontfile=Arial.ttf: text=%{n}: x=0: y=h-th: fontcolor=white: box=1: boxcolor=0x00000099" p01t02r01-60ss.mp4
ffmpeg -i p01t03r01-60s.mp4 -vf "drawtext=fontfile=Arial.ttf: text=%{n}: x=0: y=h-th: fontcolor=white: box=1: boxcolor=0x00000099" p01t03r01-60ss.mp4

# Cutting data from long csv files (120×62=7440)
head -n 7440 "p01t01r01-60s.mp4.csv" > "p01t01r01-60ss.mp4.csv"
head -n 7440 "p01t02r01-60s.mp4.csv" > "p01t02r01-60ss.mp4.csv"
head -n 7440 "p01t03r01-60s.mp4.csv" > "p01t03r01-60ss.mp4.csv"
```

## Clone demo data
```
git clone git@github.com:mxochicale/demo-data-for-sentient.git
```
