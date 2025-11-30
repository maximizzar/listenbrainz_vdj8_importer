<!--
SPDX-FileCopyrightText: 2025 maximizzar <mail@maximizzar.de>

SPDX-License-Identifier: GPL-3.0-or-later
-->
# listenbrainz_vdj8_importer

Import your VirtualDJ 8 play history into [ListenBrainz](https://listenbrainz.org/).


## Overview

`listenbrainz_vdj8_importer` is a simple command-line tool that parses **VirtualDJ 8 playlists** (`.m3u` or `.vdj`) 
and submits the tracks you've played to **ListenBrainz**, 
enabling you to keep your DJ play history synced with your ListenBrainz profile.

It uses the [`liblistenbrainz`](https://pypi.org/project/liblistenbrainz/) Python library to interact with the ListenBrainz API.

---

## Features

- Parses `#EXTVDJ` metadata lines from VirtualDJ 8 playlists
- Extracts artist, title, and play timestamps
- Displays a summary table of all listens before submission
- Submits multiple listens to ListenBrainz in one go
- Supports non-interactive and quiet modes
- Stores your ListenBrainz token in a TOML config file

## Limitations

Due to the nature of the API, 
if the combination artist and title does not match it can create unlinked plays. 
Also it may ignore title (remixer remix) and just match title if the remix isn't in the Database yet.


## Requirements

- **Python 3.10+**
- `liblistenbrainz`
- `typer`
- `tabulate`
- `toml`
- `platformdirs`

Install all dependencies via pip. 
Best create a venv.

On linux you can also add the venv's python-interpreter as a shebang.
Then you can run the script like this ./lb-vdj8-importer.py

## Configuration
Before running the importer, 
you must create a configuration file with your ListenBrainz user token.

The config file is stored in your user config directory: 
(e.g., ~/.config/listenbrainz_vdj8_importer/config.toml on Linux).

```toml
[listenbrainz]
user_token = "YOUR_LISTENBRAINZ_USER_TOKEN"
```

## Usage

Depending on how you Installed it you can do the following:

- python lb-vdj8-importer.py <path-to-playlist> [OPTIONS]
- ./lb-vdj8-importer.py <path-to-playlist> [OPTIONS]
