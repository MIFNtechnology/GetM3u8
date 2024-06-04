[![LinkGrabber](https://github.com/MIFNtechnology/GetM3u8/actions/workflows/runGrabber.yml/badge.svg?branch=main)](https://github.com/MIFNtechnology/GetM3u8/actions/workflows/runGrabber.yml)

# GetM3u8
This repo automatically converts live streams into a single .m3u8 playlist and keeps them updated. The stream URLs are stored in a text file, which a Python script parses and builds the .m3u8 file from when a GitHub action is triggered (triggered by a cron job). A direct link can then be used to get the playlist, which can then be used in an IPTV app or xTeVe.

With thanks to [@dp247](https://github.com/dp247/StreamsToM3U8) for the upgraded project.

## Supported sites
|                                                                                                                                          | Stream | EPG |
|------------------------------------------------------------------------------------------------------------------------------------------|--------|-----|
| <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1f/YouTube_light_logo_%282017%29.svg/1024px-YouTube_light_logo_%282017%29.svg.png" width="140"> | Y      | Y   |
| <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Dailymotion_logo_2023.svg/2560px-Dailymotion_logo_2023.svg.png" width="140"> | Y      | Y   |
| <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c6/Twitch_logo_%28wordmark_only%29.svg/2560px-Twitch_logo_%28wordmark_only%29.svg.png" width="140"> | Y      | Y   |

## Usage
1. Open the `streams.txt` file.
2. Add to the file with the following information for each stream:
```
Channel Name || Channel ID || Category || Channel Logo
URL
``` 
- Channel Name - the title of the channel and/or live stream. It will appear in the EPG using this name.
- Channel ID - a short identifier for the channel. Usually ends in `.XX`, where XX is the platform - e.g. `ExampleStream.yt` for YouTube streams, or `TestStream.dm` for Dailymotion ones.
- Category - the type of stream. This is used to group the channels in the playlist, so something like 'Music' or 'News' is a good idea.
- Channel Logo - URL logo.
- URL - the URL of the stream. It should be the full URL (including "https://www."), and not a shortened version (youtu.be links are not supported)

3. After saving changes, either wait for the cron job to run (this repo's job runs at 00:00, 03:00, 06:00, 09:00, 12:00, 15:00 and 18:00), or start the `LinkGrabber` workflow manually (repo > Actions tab > LinkGrabber > Run workflow).

You can also run the program locally by `python grabber.py > ./streams.m3u8` or by `chmod +x exec_grabber.sh && ./exec_grabber.sh`.

4. The .m3u8 file will be generated again.

## Files
- If you want to use this repo as your source, remember to replace the username in the below URLs:
  
|           | **Link**                                                                       |
|-----------|----------------------------------------------------------------------------|
| M3U8 file | `https://raw.githubusercontent.com/username/GetM3u8/main/streams.m3u8` |
| EPG       | `https://raw.githubusercontent.com/username/GetM3u8/main/epg.xml`      |


## Future additions
- [ ] Add in channel icons
- [ ] Rewrite `youtubeLink.txt` to be a JSON file
- ~~Support for EPG thumbnails from stream thumbnails~~
- ~~Support for TV guides/EPG matching~~

## Contributions and support
Please report the following using [Issues]([url](https://github.com/MIFNtechnology/GetM3u8/issues/new)):
- Bugs - such as something within the code breaking
- Enhancements - such as support for more sites

Please do not: 
- Report broken streams - this isn't a definitive list and is a repository that's designed to be forked!
- Attempt to make a PR with new streams - for the same reasoning as above

### Support
You can find my contact details on my profile page. Please remember that I am a solo developer and will help where I can, but please do not make demands. Reporting an issue/contacting me does not guarantee a solution/response.

