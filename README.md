a bash script to create and maintain backups of youtube playlists

I personally use this one to maintain my collection of 300+ notable videos

# features

- only downloads missing videos
- metadata, thumbnails, subtitles
- structed naming (with automatic reordering)

# needs

- **bash** (v4.0+)
- **yt-dlp** (latest recommended)
- **jq** (to process json)
- **sponge** (from moreutils)

# quick start

download the script

create directory for the playlist

```bash
mkdir playlist && cd playlist
echo "https://www.youtube.com/playlist?list=..." > url
```

run the script

```bash
yt-pl-mirror
```

# notes

## usage:

```bash
yt-pl-mirror [DIRECTORY]
```

if no directory specified, uses the current working one

## file structure

```
playlist/
├── 01 title - channel [ID].info.json # indices are zero-padded
├── 01 title - channel [ID].mkv
├── 01 title - channel [ID].webp
├── ...
├── ids # list of playlist's video ids
├── playlist.info.json
├── playlist.webp
└── url # playlist's url
```

## my yt-dlp config (for reference)

```
--cookies-from-browser firefox

--js-runtimes node
--remote-components ejs:github

--concurrent-fragments 12

--merge-output-format "mkv"
```

## automatization

you can include it into your (ana)crontab, so that it runs regularly
