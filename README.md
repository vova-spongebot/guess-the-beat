[README.md](https://github.com/user-attachments/files/33288250/README.md)# Guess the Artist

[English](README.md) | [Русский](README.ru.md)

A music quiz that runs in the browser. It plays a 30-second clip of a well-known song and you pick the artist from four options. Play solo, two players on one device, or two players over the network.

The whole project is a single file, `index.html`. No server is needed.

## How to play

1. Choose sections: **Pop**, **Rock**, **Hip-hop**, **Club electronic**. Any combination works, and tracks from the selected sections are mixed together.
2. Use the `<` `>` arrows to set the number of rounds (1 to 50, default 10).
3. Press **1 PLAYER** or **2 PLAYERS**.
4. Listen to the clip and pick the artist with a button or the `1`–`4` keys.

## Scoring

- A correct answer is worth up to 1000 points. The value drops while you think and falls to 100 after 20 seconds, so faster answers score more.
- A wrong answer or running out of time gives 0 points.
- **Remove 2** hides two wrong options but halves the points for that question.

## Two players

- On one device, players answer in turns.
- The **Finish** button ends the game early.
- At the end you get a final standings table (place, points, number of correct answers) and a round-by-round table.

## Network play

1. Both players open `index.html` (it is easiest to host the game on GitHub Pages and share the link).
2. The first player presses **CREATE ROOM** and gives the 5-character code to the second player.
3. The second player enters the code and presses **JOIN**.

The first player runs the game, and the second sees the same screen and answers on their own device during their turn. The connection goes directly between browsers through [PeerJS](https://peerjs.com/), so an internet connection is required. In strict corporate networks the connection may fail to establish.

## Where the tracks come from

- **Last.fm**: the most popular tracks for a genre tag (for example `house`, `rock`, `hip-hop`).
- **Apple Music (iTunes Search API)**: 30-second previews, plus a genre check so a track does not end up in the wrong section.

Each track appears at most once per session.

## Limitations

- Last.fm does not say whether a track ever charted. "Well known" is based on how popular the track is within a tag, so it is an approximation.
- Apple Music genres are coarse (usually just Electronic or Dance), so related styles occasionally slip into the electronic section.
- If Apple has no preview for a track, it is skipped.
- If Last.fm is unavailable, the game falls back to searching Apple Music, and the selection of hits is worse.

## Your own Last.fm key

The game contains a Last.fm API key (the `LASTFM_KEY` constant in `index.html`). Anyone who opens the file can see it. If you publish the game, create your own free key at <https://www.last.fm/api/account/create> and replace the value.
