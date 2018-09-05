# AWK
Abk. für. Alfred V. **A**ho, Peter J. **W**einberger und Brian W. **K**ernighan

## Grundgerüst
```awk

awk '
	/* Block der VOR dem einelsen der Dateien
	   ausgeführt wird */	
	BEGIN {
		<commands>
	}
	
	/<regExpA>/ {
		<commands>		
	}
	
	/<regExpB>/ {
		<commands>		
	}
	...

	/* Block der NACHDEM einlesen der Dateien
	   ausgeführt wird
	END {
		<commands>
	}

' </path/to/filename>
```