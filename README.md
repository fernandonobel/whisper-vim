# whisper-vim

`whisper-vim` integrates OpenAI's Whisper into VIM's text editor so you can transcribe your voice to text with a single keystroke.

## Usage

* In normal mode, press `Ctrl-X` to start recording your voice.
* Press `Ctrl-C` to stop recording and start transcribing it into text.
* The trascribed text will be pasted below the cursor.

## Features

- Uses the API of whisper, so transcription should be fast independent of your computer.
- Easy-to-installation.
- Easy-to-use.
- Easy-to-modify.

## Installation

You need to install `sox` and `whisper-cli`:

```sh
sudo apt-get install sox
pip install whisper-cli
```

Then you need to add you API to whisper-cli.

```sh
whisper key set <openai_api_key>
```

If you have problems installing or configurating `whisper-cli`, please check its GitHub repository: https://github.com/vatsalaggarwal/whisper-cli

Lastly you have to copy `whisper-cli` to you bin folder.

```sh
cp whisper-vim ~/bin/whisper-vim
```

And add this mapping to your vim.rc:

```vim
nnoremap X :!whisper-vim record<CR>:!whisper-vim transcribe<CR>:let @a = system("cat /tmp/whisper-recording.txt")<CR>"ap
```

## Contribute

Feel free to contribute :-)

## Support

If you are having issues, please let me know as an Issue in this repository.

## License

The project is licensed under the MIT license.
