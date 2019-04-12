# Lichess Bot

This is a little bot playing hyperbullet (30s per game) on lichess.org.

It makes use of puppeteer to communicate with a chromium browser and to get the last moves from the dom. It currently polls the DOM for move updates which is easy to implement but bad design because it's slow.

### Installation

1. You need a recent version of `npm` and `node` installed on your computer.
2. Then clone this repo and change into the directory.
3. Install dependencies with `npm install`. This will download puppeteer and a local chromium browser (around 120MB)
3. Compile stockfish or download a binary and remember the path to the stockfish binary.
4. Modify the settings in the top of `index.js`:

```js
// by default the bot challenges the player again after the game
// when the challenge is not accepted, a new game is seeked
const config = {
    stockfish_binary_path: 'Stockfish/src/stockfish',
    maxGames: 5,
    only_one_game_per_player: false,
    movetime: [100, 300], // picks a random movetime in ms in this interval
};
```

Then start the bot by calling it in a command line using this line:

```
LICHESS_USER=your_lichess_account LICHESS_PWD=your_lichess_password node index.js
```

I hope calling it like this works on Windows. If not, just hardcode the user login and password. If you don't manage to do that, you probably have legitimate reasons to cheat :D

### Features

1. Plays completely autonomous and challenges the opponent until she had enough. Then seeks for a new game.
2. You can specify the following settings in the `index.js` file in the `config` variable.
3. Picks a random move suggestion by the engine. Doesn't always play the best move.

### Limitations

1. Has problems promoting. Just change the lichess settings to autoqueen to fix that.
2. Gets detected rather quickly because it's too strong
3. Improvement: Add a mode to highlight the engine moves instead of playing them automatically. Then you can decide on your own if you want to make the bad bad engine move ;)

### Why?

Cheating sucks, no doubt. But I got triggered when playing some cheaters in the high hyper bullet range.


