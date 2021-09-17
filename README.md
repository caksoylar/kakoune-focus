# kakoune-focus
`kakoune-focus` is a plugin to let you work on multiple selections more efficiently by hiding lines that are far from your selections using Kakoune's `replace-ranges` highlighter (`:doc highlighters specs-highlighters`).

![demo](https://caksoylar.github.io/kakoune-focus/focus.gif)

## Installation
You can copy `focus.kak` to your `autoload` folder, e.g. into `~/.config/kak/autoload`.

If you are using [plug.kak](https://github.com/andreyorst/plug.kak):
```kak
plug "caksoylar/kakoune-focus" config %{
     # configuration here
}
```

## Usage
Once you have the (ideally multiple) selections you want to focus on, use `focus-selections` to hide the surrounding lines. You can use `focus-clear` to disable this or use `focus-toggle` to toggle it on and off.

I recommend assigning a mapping for easy access, for example `,<space>` to toggle:
```kak
map global user <space> ': focus-toggle<ret>' -docstring "toggle selections focus"
```

## Configuration
There are a couple of options you can configure:
- `focus_separator (str)`: What string to use as the separator to replace hidden lines, can use markup strings `:doc faces markup-strings`
- `focus_context_lines (int)`: How many lines of context to preserve above and below selections (default: 1)

## Caveats
Due to [a Kakoune shortcoming](https://github.com/mawww/kakoune/issues/3644) with the `replace-ranges` highlighter, some lines can be visually cut off from the bottom after focusing. This seems to be an issue especially when long spans of lines are hidden and soft line wrapping is enabled with the `wrap` highlighter.

## License
MIT
