# SVG Awesome

This is a simple setup for creating an SVG `<symbol>` sprite from [Font Awesome's](https://fortawesome.github.io/Font-Awesome/) SVG font.

## Steps

1. Download Font Awesome from <https://fortawesome.github.io/Font-Awesome/>.
2. Replace the contents of _svg-awesome.icons.kit_ with the `<glyph>`s from Font Awesome's _fonts/fontawesome-webfont.svg_, starting at the glyph for unicode `&#xf000;` (~ln. 35).
3. In _svg-awesome.icons.kit_:
	* Find `<glyph\ unicode="&#x(.*?);"\ (horiz-adv-x="(.*?)" )?d="(.*?)"\ />` and replace with `<symbol\ id="<!-- @x\1 -->"\ viewBox="0\ 0\ 1792\ 1792"\ data-unicode="&#x\1;"\ data-horizadvx="\3" preserveAspectRatio="true"><title><!-- @x\1 --></title><path\ d="\4"/></symbol>`.
	* Find `<glyph\ (.*?)/>\s` and replace with `''` to remove empty `<glyph>` definitions.
4. Replace the contents of _svg-awesome.chars.kit_ with the character variables from Font Awesome's _less/variables.less_, starting at the first variable that starts with `@fa-var-` (~ln. 14).
5. In _svg-awesome.chars.kit_:
	* Find `@fa-var-(.*?):\ "\\(.*?)";` and replace with `<!-- @x\2: \1 -->`.
6. If you haven't already, process _svg-awesome.kit_.
7. If the file you created isn't an SVG, replace whatever extension it has with `.svg`.
8. Enjoy your new SVG Awesome icons.

## Requires

* A text editor or file processor that's capable of regex find and replace.
* A Kit compiler. The easiest is the original, [CodeKit](https://incident57.com/codekit/). If you're aware of any others, hit me up and I'll check them out and link them here if they're good.
