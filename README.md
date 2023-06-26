# Quotable

Quotable is an intuitive application designed to generate accurate subtitles for TV shows, movies and other video media using a combination of webscraping and speech-to-text. It's written in Python and incorporates a user-friendly API, command line interface and options for implanting subtitles directly into video or saving as an srt file.

## Requirements
- [Picovoice Access Key](https://picovoice.ai/)
- [ffmpeg](https://ffmpeg.org/)

Picovoice is a company specializing in speech-related AI processing. PvLeopard, their speech-to-text engine, serves as the backend for Quotable. In order to use Quotable, you must first navigate to their website and sign up for a free account. You can then obtain an access key and make use of up to a 25 free processing hours per month.

## Usage
```python
from quotable import Quotable

q = Quotable(access_key)

# process TV show (file, show, episode)
show = q.load_show('video1.mp4', 'Corner Gas', 'The Littlest Yarbo')

# process movie (file, movie)
movie = q.load_movie('video2.mp4', 'Madagascar')
```
In some cases, Quotable may be unable to locate a transcript for the provided media, in which case it will throw an error. You may have to provide your own transcript.
```python
transcript = [
    "Last week, Japanese scientists explaced...",
    "placed explosive detonators at the bottom of Lake Loch Ness...",
    "to blow Nessie out of the water.",
    "Sir Curt Godfrey of the Nessie Alliance...",
    "summoned the help of Scotland's local wizards...",
    "to cast a protective spell over the lake and its local residents...",
    "and all those who seek for the peaceful existence of our underwater ally."
]

# process video media (file, transcript)
q.load_custom('video3.mp4', transcript)
```
Quotable can save subtitles as part of a video file or as a seperate srt file.
```python
show = q.load_show('video4.mp4', 'I Love Lucy', 'Job Switching')

# will overwrite original file, 'video4.mp4'
show.save_as_file()

# will derive file name from video file, 'video4.srt'
show.save_as_srt()

# an alternative file name can be specified
show.save_as_file('new_video.mp4')
show.save_as_srt('new_video.srt')
```
Finally, Quotable has the ability to save as a serialized object, or quote. These files are useful as they allow you to keep from having to reprocess files. You can save these in order to debug or quickly reprocess with future versions of Quotable.
```python
movie = q.load_movie('video5.mp4', 'Rear Window')

# saves with file extension '.qot' by default, will save as 'video5.qot'
movie.save_as_quote()

# load from quote
reloaded = q.load_quote('video5.qot')
```
## Conclusion
If you have any questions, problems or feedback, please don't hesitate to raise an issue. Thanks very much for your patronship. Additional documentation can be found at [getting to it].
