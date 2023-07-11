# whisper-vim

`whisper-vim` integrates OpenAI's Whisper into VIM's text editor so you can transcribe your voice to text with a single keystroke.

https://github.com/fernandonobel/whisper-vim/assets/30172734/1ddf97b9-e90d-4277-aed6-b7b5b8c01773

## Usage

* In `NORMAL` mode, press `Ctrl-X` to start recording your voice.
* Press `Ctrl-C` to stop recording.
* The trascribed text will be pasted below your cursor.

## Features

`whisper-vim` is just a bash script that calls `sox` to record your voice and then calls `whisper-cli` to use Whisper's OpenAI API to transcript the audio into text. Lastly, you have a mapping in VIM to call this script easily. 

Advantages:

- Easy-to-install: you don't need to install whisper locally.
- Easy-to-use: the recording and transcription process is as easy as it gets.
- Easy-to-modify: it is just a bash script and a VIM mapping.

Disadvantages:

- You need a OpenAI key, which you have to spend money, but you have 5€ for free to test it.
 
## Installation

First, install `sox` and `whisper-cli`:

```sh
sudo apt-get install sox
pip install whisper-cli
```

(I have used `python3.10` for installing `whisper-cli`.)

Second, add you OpenAI API key to `whisper-cli`:

```sh
whisper key set <openai_api_key>
```

If you have problems installing or configurating `whisper-cli`, please check its GitHub repository: https://github.com/vatsalaggarwal/whisper-cli

Third, add `whisper-vim` to you `bin` folder.

```sh
git clone https://github.com/fernandonobel/whisper-vim
cd whisper-vim
cp whisper-vim ~/bin/whisper-vim
```

Finally, add this mapping into your `.vimrc`:

```vim
nnoremap X :!whisper-vim record<CR>:!whisper-vim transcribe<CR>:let @a = system("cat /tmp/whisper-recording.txt")<CR>"ap
```

## Contribute

Feel free to contribute :-)

## Support

If you are having issues, please let me know as an Issue in this repository.

## License

The project is licensed under the MIT license.
