---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public

- First Envelope is always an automation for the loudness

# Sound Design
### Filter
- Aktivieren
- Auf Low-Pass setzen
- Ein wenig Drive
- Cutoff setzen

![[Screenshot 2024-10-27 at 10.25.00.png]]

### Envelope 1
- Attack: 0 MS
- Hold: some MS
- Decay: 0ms
- Sustain: 0db
- Release: ~500 ms

![[Screenshot 2024-10-27 at 10.24.33.png]]
### Envelope 2
- Auf Cutoff des Filters legen
- Attack: 0 MS
- Hold: as preferred
- Decay: ~450ms
- Sustain: 0db
- Release: ~1000 ms
- 
![[Screenshot 2024-10-27 at 10.24.46.png]]


### Oscillators
Typical: Square as base, Saw on top for harmonics
#### OSC 1
- Choose: Analog > Basic Shapes
- VT Pos: Square
- Unison: 3
- Detune:
- Octave: -3
- Rand: 0 (Set Phase for each note to default)

 ![[Screenshot 2024-10-27 at 10.24.51.png]]

#### OSC 3
- Choose: Analog > Basic Shapes
- VT Pos: Saw
- Octave: -2
- - Rand: 23% (Set Phase for each note to 23% Random)

![[Screenshot 2024-10-27 at 10.24.55.png]]

### Noise
- Aktivieren
- Noise Type: z.B. Analog > Ping
- Level: mit ENV2 automatisieren
- Filter: In den Filter hinein geben (N)

![[Screenshot 2024-10-27 at 10.41.51.png]]
### EFX
- Hyper / Dimension: Adds some Room
	- Hyper is more digital
	- Dimension is more natural
- Reverb:
	- Size: 0
	- Decay: 0
	- Mix: 
		- Automated by ENV2
		- Default on 0
		- Automation Only added on tail
	- 
- EQ:
	- Gain: mit ENV2 automatisieren
	- EQ Type: Peak
	- Q: Anpassen
	- Freq: Anpassen


![[Screenshot 2024-10-27 at 10.25.13.png]]

### Makro Efx
- Multiband Compression: Bringt den Sound mehr "zusammen"
- EQ Eight: Damit man das Freq Spektrum sieht
	- Sweet Spot finden
	- High freq etwas heraus nehmen
- Compressor: [[Side-Chaining]] to ghost kick
- Limiter: 
	- Avoid Clipping
	- Push it more and compress it
	- Ceiling:  Anpassen
- Auto Filter
	- Von Kick kopieren

![[Screenshot 2024-10-27 at 10.52.30.png]]
# Bass line
- In Tech House typically semitone above - wholetone below root note
- Add some 16th syncopation

 
### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

