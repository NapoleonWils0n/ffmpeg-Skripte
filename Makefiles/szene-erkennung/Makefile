# ffmpeg Makefile zur Szenenerkennung

# Verschieben Sie dieses Makefile in dasselbe Verzeichnis wie das zu verarbeitende Video

# Sie müssen dem Makefile den Namen des zu verarbeitenden Videos mitteilen
# entweder durch Bearbeiten des Makefiles und Ändern von input.mp4 in den Namen des zu verarbeitenden Videos
# und dann läuft: make

# oder durch Ausführen von: make input=filename.mp4
# wobei filename.mp4 der Name der zu verarbeitenden Datei ist

# make clean: fordert Sie auf, Textdateien und Videoclips mit Ausnahme der Eingabedatei zu entfernen

# change input.mp4 to the file name to process
# ändern Sie Eingang.mp4 in den zu verarbeitenden Dateinamen
input := eingang.mp4

# all - führen Sie das geschnittene Rezept aus, das ausgeführt wird szene-erkennen, szene-zeit Und szene-geschnitten in Ordnung
all: schneiden

# szene-erkennen - erkennung ist die Voraussetzung
erkennen: $(input)
	@szene-erkennen -i $(input) -o erkennung.txt


# scene-zeit - erkennen ist die Voraussetzung
zeit: erkennen
	@szene-zeit -i erkennung.txt -o schnittliste.txt


# szene-geschnitten - Zeit ist die Voraussetzung
schneiden: zeit
	@szene-geschnitten -i $(input) -c schnittliste.txt


# make clean - Aufforderung zum Entfernen von Textdateien und Videoclips mit Ausnahme der Eingabedatei
.PHONY: clean
clean:
	rm -fI schnittliste.txt erkennung.txt $(wildcard *-[0-9]*.mp4)
