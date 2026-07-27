## A simple YouTube playlist downloader and player in Bash

Playlist is very simple and folder based.
It uses yt-dlp and VLC to download and play videos.
A playlist is essential all the playable files in the current working directory with the specified format below.
A playable file is any file VLC can play.
All the metadata is stored in the file name.
It has the format:

```
<index> <bitmask> [<id>] <name of file>.<ext>
```
- index: The order the videos will play from 1-999. (It's fixed at 3 digits for now.)
- bitmask: A bitmask of whether the video has been watched. (Other masks are reserved for later use.)
- id: The UUID of the video given by YouTube.
- name of file: Self-explanatory.
ext: the format extention of the video.

To download a playlist use the `link` sub-command to store the YouTube playlist link into the `PLAYLIST_DOWNLOAD_LINK` file.

```bash
playlist link "https://youtube.com/playlist?list=PLdPwyUeH0mS566Y0YZ7oAGghzMgRlWTBf&si=ZtFh0qmKbTPnDXPg"
```

To download the video you use the `download` sub-command. This sub-command will only play videos that are not marked as `watched`.

```bash
playlist download
```
To play the videos use the `play` sub-command in the folder the video files are in.

```bash
playlist play
```

Videos are marked played once the play cursor reaches near the end of the video.

You can also mark videos as watched with the `mark` sub-command.

```bash
playlist mark <index>
```

You can also mark a range of video at once. (The range is inclusive)

```bash
playlist mark <start index>-<end index>
```

You can unmark videos as unwatched with the `unmark` sub-command.

```bash
playlist unmark <index>
```

You can also unmark a range of video at once. (The range is inclusive)

```bash
playlist unmark <start index>-<end index>
```

You can list the videos in a nicer format with the `list` sub-command.

```bash
playlist list
```

A playlist can also be created from videos not downloaded from YouTube.
This will add the required metadata to the file name. It adds the files in normal sorted order.

```bash
playlist make
```

You can easily change the order of the videos with the `move` sub-command.
This will rename all the files in the proper order for you.

```bash
playlist move <from index> <to index>
```
It can also move a range of videos.

```bash
playlist move <start from index>-<end from index> <to index>
```

Many playlist on YouTube seem to be in reverse order. You can use the `reverse` sub-command to reverse the playlist.

```bash
playlists reverse
```
