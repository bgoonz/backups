# Audio Projects

[https://bgoonz-blog.netlify.app/docs/audio/](https://bgoonz-blog.netlify.app/docs/audio/)

1. **[About This Site](https://bgoonz-blog.netlify.app/docs/audio/about.html)** ([ipynb](https://bgoonz-blog.netlify.app/docs/audio/about.ipynb)) Start here!
2. [About the CCRMA Workshop on Music Information Retrieval](https://bgoonz-blog.netlify.app/docs/audio/about_ccrma_workshop.html) ([ipynb](https://bgoonz-blog.netlify.app/docs/audio/about_ccrma_workshop.ipynb))
3. [What is MIR?](https://bgoonz-blog.netlify.app/docs/audio/why_mir.html) ([ipynb](https://bgoonz-blog.netlify.app/docs/audio/why_mir.ipynb))
4. [SoX and ffmpeg](https://bgoonz-blog.netlify.app/docs/audio/sox_and_ffmpeg.html) ([ipynb](https://bgoonz-blog.netlify.app/docs/audio/sox_and_ffmpeg.ipynb))
5. [Alphabetical Index of Terms](https://bgoonz-blog.netlify.app/docs/audio/alphabetical_index.html) ([ipynb](https://bgoonz-blog.netlify.app/docs/audio/alphabetical_index.ipynb))
6. [Short-time Fourier Transform and Spectrogram](https://bgoonz-blog.netlify.app/docs/audio/stft.html) ([ipynb](https://bgoonz-blog.netlify.app/docs/audio/stft.ipynb))
7. [Video: Chroma Features](https://bgoonz-blog.netlify.app/docs/audio/video_chroma.html) ([ipynb](https://bgoonz-blog.netlify.app/docs/audio/video_chroma.ipynb))
8. [Onset-based Segmentation with Backtracking](https://bgoonz-blog.netlify.app/docs/audio/onset_segmentation.html) ([ipynb](https://bgoonz-blog.netlify.app/docs/audio/onset_segmentation.ipynb))

# Determining the key of BWV1001 - 1st Movement, Adagio

Let's get weird with Bach: find the key of BWV10001 just by loading and parsing the MIDI file.

[Audio%20Proj%20b12ba/1650fd57388f8c60c592727a076ad22bffc6e534cb3ff2e3c3387da7f2e902560a81750c910d57b76d3328ce1a1158a8b3ddff303558bac8555b09983dd3b992](Audio%20Proj%20b12ba/1650fd57388f8c60c592727a076ad22bffc6e534cb3ff2e3c3387da7f2e902560a81750c910d57b76d3328ce1a1158a8b3ddff303558bac8555b09983dd3b992)

I'm loading [these MIDI files](https://archive.org/details/BachsSoloViolinWorks/David_J_Grossman_-_BWV1001_-_1st_Movement_-_Adagio.mp3), from a separate server because the Internet Archive doesn't do CORS requests.

We're looking at BWV1001 - 1st Movement, Adagio, by [Johann Sebastian Bach](https://en.wikipedia.org/wiki/Johann_Sebastian_Bach).

Load a MIDI file and convert it using [MIDIConvert](https://github.com/Tonejs/MidiConvert) to get a nice JSON representation. MIDI is both a real-time protocol, a physical connector, and a file format: this is the file format, a format that contains musical information.

Unlike MP3 and its descendents, MIDI stores individual notes and instruments that your computer recreates when it plays the file - it does not store the sound waves. Which is bad for the texture of the music - MIDI files have a characteristic cheesiness - but great for doing quick music analysis.

Chart all the notes. I'll use vega-lite for this. MIDI has a 'note' representation that's just a number, because computers store everything as numbers, at the lowest level.

First, combine all notes from all instruments. We don't particularly care which instrument makes which tone in this case.

Now I want to get a feeling for the key: the notes in this piece, by number of appearances, irregardless of octave, translated from their MIDI numbers into note names.

It's neat that all 12 tones get some representation: playing *only* the notes in a key would give a subset of this. But ranking only by incidence might be misleading: let's instead show them by total duration, so [nonchord tones](https://en.wikipedia.org/wiki/Nonchord_tone) are more obvious.

In the chart above, I'm doing the summation of duration in Vega, the charting library, itself. To get the top notes, I'll need that value in JavaScript:

The seven top notes of this lovely tune are G, D, A#, A, C, D#, and F. Now, you can go much deeper on this - but in broad strokes, and for many instruments and musicians, A# is the same as B♭, and D# is the same as E♭. So, with those substitutions, the top notes are:

G, A, B♭, C, D, E♭, F

And those are the notes in [G minor](https://en.wikipedia.org/wiki/G_minor).
