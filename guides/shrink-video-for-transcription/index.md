> One ffmpeg command turns a gigabyte screen recording into a tiny speech file any transcriber accepts, with bitrate math, upload caps, trims, and batch runs.
>
> Source: https://christopherabraham.com/guides/shrink-video-for-transcription/ · Updated 2026-10-31 · By Christopher Abraham

# How to shrink a huge video to the smallest audio file that still transcribes

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 31, 2026

Every transcription tool listens and nothing more, from a web upload box to a speech model on your own laptop. A screen recording or a meeting export carries gigabytes of picture the transcriber throws away. I had a 5.9 GB MP4 of a recorded conversation, and a single ffmpeg command turned it into an audio file of roughly 11 MB per hour that transcribed cleanly. Here is that command, what each flag does, and how I tune it for wherever the file goes next.

## What a transcriber actually hears

Whisper, the open speech model inside most of today's transcription products, resamples every file it receives to one channel at 16,000 samples per second before it does anything else. Stereo, 48 kHz audio, and generous bitrates are bytes the model discards on arrival. That gives the target: mono, 16 kHz, encoded with a codec designed around the human voice. Anything more is upload time and storage you pay for and the model never uses.

It also means the original video stays the master. I keep it until the transcript checks out, then decide whether the picture is worth archiving at all.

## Open a terminal

Everything in this guide is typed into a terminal, the text window where you give your computer commands. Open one this way:
- **Linux Mint and Ubuntu:** press Ctrl+Alt+T, or open the menu and type Terminal.
- **macOS:** press Cmd+Space, type Terminal, and press Return.
- **Windows 10 and 11:** right click the Start button and choose Terminal or Windows PowerShell.

You type or paste a command at the prompt and press Enter. In a Linux terminal, paste with Ctrl+Shift+V; on a Mac, Cmd+V; in Windows Terminal, Ctrl+V or a right click.

## Install ffmpeg

ffmpeg is the free command line converter that sits underneath nearly every other audio and video tool. First see whether you already have it:

```
ffmpeg -version
```

If a version banner prints, skip to the next section. If you see "command not found" or "not recognized," install it with the line for your system:

```
# Linux Mint, Ubuntu, Debian
sudo apt install ffmpeg

# macOS with Homebrew
brew install ffmpeg

# Windows
winget install Gyan.FFmpeg
```

A few notes so nothing surprises you:
- **On Linux,** `sudo` asks for your own login password, and nothing appears while you type it. Type it anyway and press Enter, then answer `Y` when apt asks to continue. If apt says it can't find the package, run `sudo apt update` first and try again.
- **On a Mac,** the `brew` command comes from Homebrew. If the Mac answers "command not found: brew," install Homebrew with the one line shown on [its home page](https://brew.sh/), then run the ffmpeg line.
- **On Windows,** winget is built into current versions of Windows 10 and 11. When it finishes, close the terminal and open a new one, because the old window doesn't know the new program exists yet.

Run `ffmpeg -version` again. The banner means you're ready. While you're there, confirm your build can write Opus, the codec the main command uses:

```
ffmpeg -hide_banner -encoders | grep libopus
```

On Windows, swap `grep libopus` for `findstr libopus`. One matching line means you're set. The standard builds for all three systems include it; if yours prints nothing, use the MP3 version further down.

## Go to your recording

The terminal works in one folder at a time. Move it to the folder that holds your video and list what's there:

```
cd ~/Videos
ls
```

Recordings often land in Videos, Downloads, or Desktop, so swap the folder name as needed. On Windows the same commands work in PowerShell, as in `cd $HOME\Videos` followed by `ls`. A shortcut on every system: type `cd` and a space, drag the folder from your file manager into the terminal window, and press Enter.

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

Replace both file names with your own, keeping the quotes so names with spaces work. ffmpeg prints a running status line while it works; the `time=` figure counts up through the recording, and the prompt returns when it's done. Check the result:

```
ls -lh *.opus
```

The size should read a few megabytes per hour. Open the file in any media player and listen for a few seconds to confirm the voices came through. My 5.9 GB file came out at well under one percent of its original size, and the transcript lost nothing.

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

Run it from inside the folder of recordings. `-n` refuses to overwrite, so any recording that already has an `.opus` beside it is skipped. I can rerun the loop safely every time new recordings land in the folder.

## Make it one word

The folder loop above and this shortcut are for Linux and macOS. I add a small function to my shell's settings file so I never retype the flags. Open that file in nano, a simple editor that runs inside the terminal:

```
# Linux
nano ~/.bashrc

# macOS
nano ~/.zshrc
```

Hold the down arrow to reach the bottom, paste this line, save with Ctrl+O and Enter, then exit with Ctrl+X:

```
toaudio() { ffmpeg -i "$1" -vn -ac 1 -ar 16000 -c:a libopus -b:a 24k -application voip "${1%.*}.opus"; }
```

Load the change into the open window with `source ~/.bashrc` (or `source ~/.zshrc` on a Mac). New terminals pick it up on their own. From then on the whole conversion is:

```
toaudio "recording.mp4"
```

On Windows, the same idea works as a PowerShell loop over a folder:

```
Get-ChildItem *.mp4 | ForEach-Object { ffmpeg -n -i $_.Name -vn -ac 1 -ar 16000 -c:a libopus -b:a 24k -application voip ($_.BaseName + ".opus") }
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
