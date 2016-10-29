# Plex Audio Tracks

A shell script designed to run directly on a Unix/Unix-like Plex Media Server instance to identify media files with an unknown audio laguage and correctly label with the appropriate language code. In most cases, this can be done by remuxing the media file rather than having to re-encode. This script supports MP4 (mp4box) and MKV (mkvpropedit) to modify audio tracks.

This script can also work across files that are stored on CIFS or external shares, providing the appropriate permissions are set.

### Prerequisites

* Bash
* sqlite3
* mp4box
* mkvtoolnix
* mkvmerge

### About this script

Plex Media Server is a system driven largely by metadata and this is often derived from media files themselves. Often, you may find media files with "Unknown Audio", while this won't prevent playback, more often than not any unknown audio track will cause any available subtitles for a media file to be automatically displayed which can be annoying. This script will identify media files without a language set on an audio track and edit accordingly.

This script performs a single `SELECT` query on the Plex Media Server database in order to identify such files, it does not perform any write or `UPDATE` query. You may see examples of users overwriting the metadata in the Plex Media Server database itself. I would strongly discourage this approach, as you are essentially patching over a problem with a temporarily solution, you should correct the file properties directly in order for Plex Media Server to automatically a scan a file with the correct information.
