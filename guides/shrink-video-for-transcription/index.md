> One ffmpeg command turns a gigabyte screen recording into a tiny speech file any transcriber accepts, with bitrate math, upload caps, trims, and batch runs.
>
> Source: https://christopherabraham.com/guides/shrink-video-for-transcription/ · Updated 2026-10-31 · By Christopher Abraham

# How to shrink a huge video to the smallest audio file that still transcribes

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 31, 2026

Every transcription tool listens and nothing more, from a web upload box to a speech model on your own laptop. A screen recording or a meeting export carries gigabytes of picture the transcriber throws away. I had a 5.9 GB MP4 of a recorded conversation, and a single ffmpeg command turned it into an audio file of roughly 11 MB per hour that transcribed cleanly. Here is that command, what each flag does, and how I tune it for wherever the file goes next.

## What a transcriber actually hears

Whisper, the open speech model inside most of today's transcription products, resamples every file it receives to one channel at 16,000 samples per second before it does anything else. Stereo, 48 kHz audio, and generous bitrates are bytes the model discards on arrival. That gives the target: mono, 16 kHz, encoded with a codec designed around the human voice. Anything more is upload time and storage you pay for and the model never uses.

It also means the original video stays the master. I keep it until the transcript checks out, then decide whether the picture is worth archiving at all.

## Install ffmpeg

ffmpeg is the free command line converter that sits underneath nearly every other audio and video tool. Install it once:

```
# Linux Mint, Ubuntu, Debian
sudo apt install ffmpeg

# macOS with Homebrew
brew install ffmpeg

# Windows
winget install Gyan.FFmpeg
```

Before converting, I check the running time in seconds, which tells me how big the output will be:

```
ffprobe -v error -show_entries format=duration -of csv=p=0 "recording.mp4"
```

## The command

```
ffmpeg -i "recording.mp4" -vn -ac 1 -ar 16000 -c:a libopus -b:a 24k -application voip "recording.opus"
```
- `-i "recording.mp4"` names the input. Keep the quotes whenever the name has spaces.
- `-vn` discards the video stream.
- `-ac 1` folds the sound down to a single channel.
- `-ar 16000` resamples to 16 kHz, the rate the model listens at.
- `-c:a libopus` encodes with Opus, the codec inside modern voice and video calls.
- `-b:a 24k` sets 24 kilobits per second.
- `-application voip` tells Opus to favor intelligible voices over music.

My 5.9 GB file came out at well under one percent of its original size, and the transcript lost nothing.

## Pick a bitrate

Size is bitrate multiplied by running time, so the arithmetic is easy. For one hour of speech:
- `-b:a 16k` comes to about 7 MB. Enough for one clear voice in a quiet room.
- `-b:a 24k` comes to about 11 MB. My default for meetings, interviews, and calls.
- `-b:a 32k` comes to about 14 MB. I use it for echoing rooms, strong accents, and people talking over each other.

Under 16k, the model starts missing mumbled words and the short replies buried in crosstalk. The savings are not worth a worse transcript.

## When a service refuses Opus

Some upload forms judge a file by its extension. Opus normally lives inside an Ogg container, so naming the output `.ogg` gets it past many of them with no other change:

```
ffmpeg -i "recording.mp4" -vn -ac 1 -ar 16000 -c:a libopus -b:a 24k -application voip "recording.ogg"
```

MP3 is accepted everywhere. It needs a little more bitrate to stay as clear:

```
ffmpeg -i "recording.mp4" -vn -ac 1 -ar 16000 -c:a libmp3lame -b:a 32k "recording.mp3"
```

For apps in the Apple and Microsoft worlds that want M4A:

```
ffmpeg -i "recording.mp4" -vn -ac 1 -ar 16000 -c:a aac -b:a 32k "recording.m4a"
```

## Fit under an upload cap

Transcription APIs and web apps limit the size of a single upload. OpenAI's speech to text API has capped files at 25 MB for a long time, so check the current figure for whatever you use. At 24k Opus, 25 MB holds a little over two hours. For anything longer, I cut the audio into hour pieces without encoding it again:

```
ffmpeg -i "recording.opus" -f segment -segment_time 3600 -c copy "recording-part-%02d.opus"
```

Because `-c copy` only rewraps the existing audio, the split takes seconds and costs no quality.

## Keep only the part you need

Most recordings open with setup chatter. To skip the first ten minutes and keep the next thirty five:

```
ffmpeg -ss 00:10:00 -i "recording.mp4" -t 00:35:00 -vn -ac 1 -ar 16000 -c:a libopus -b:a 24k -application voip "excerpt.opus"
```

Placing `-ss` ahead of `-i` jumps straight to that point instead of decoding everything before it, which matters on a long file.

## Convert a whole folder

```
for f in *.mp4; do
  ffmpeg -n -i "$f" -vn -ac 1 -ar 16000 -c:a libopus -b:a 24k -application voip "${f%.*}.opus"
done
```

`-n` refuses to overwrite, so any recording that already has an `.opus` beside it is skipped. I can rerun the loop safely every time new recordings land in the folder.

## Make it one word

I add this to the end of `~/.bashrc` (or `~/.zshrc` on a Mac) and run `source ~/.bashrc` once:

```
toaudio() { ffmpeg -i "$1" -vn -ac 1 -ar 16000 -c:a libopus -b:a 24k -application voip "${1%.*}.opus"; }
```

From then on the whole conversion is:

```
toaudio "recording.mp4"
```

## Then transcribe it

The small file goes anywhere: a paid service, an API, or a copy of Whisper running on your own machine with nothing uploaded. If you publish audio or video, a reviewed transcript is also plain text that search engines and AI assistants can read and quote, which is why I treat it as part of the page and not an afterthought. For how episode text spreads across the web once it is published, read [the show notes cascade](https://christopherabraham.com/guides/show-notes-cascade/).

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [FFmpeg codecs documentation](https://ffmpeg.org/ffmpeg-codecs.html)
- [OpenAI Whisper](https://github.com/openai/whisper)
- [Opus codec](https://opus-codec.org/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
