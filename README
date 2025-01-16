This file is in UTF-8 encoding.

To use unicode utility, you need: 
 - python3
 - there is still some python2 compatibility, but now it is unsupported (and will fail when UnicodeData.txt is compressed)
 - (recommended) UnicodeData.txt file in /usr/share/unicode/, ~/.unicode/ or current
   working directory.
    - apt-get install unicode-data  # Debian
    - dnf install unicode-ucd       # Fedora
    - unicode --download            # try to download the file
 - if you want to see Unicode block information, you also need
   Blocks.txt file, which you should put into /usr/share/unicode/,
   ~/.unicode/ or current working directory.
 - if you want to see UniHan properties, you need also Unihan.txt file
   which should be put into /usr/share/unicode/, ~/.unicode/ or
   current working directory.


Enter a Python regular expression, hexadecimal number or some characters as an
argument. unicode will try to guess what you want to look up, see the manpage
if you want to force other behaviour (the manpage is also the best
documentation). In particular, -r forces searching for regular expressions in
the names of characters, -s forces unicode to display information about the
characters given.

Here are just some examples:

$ unicode euro
U+20A0 EURO-CURRENCY SIGN
UTF-8: e2 82 a0   UTF-16BE: 20a0   Decimal: &#8352;
₠
Category: Sc (Symbol, Currency)
Bidi: ET (European Number Terminator)

U+20AC EURO SIGN
UTF-8: e2 82 ac   UTF-16BE: 20ac   Decimal: &#8364;
€
Category: Sc (Symbol, Currency)
Bidi: ET (European Number Terminator)

$ unicode 00c0
U+00C0 LATIN CAPITAL LETTER A WITH GRAVE
UTF-8: c3 80   UTF-16BE: 00c0   Decimal: &#192;
À (à)
Lowercase: U+00E0
Category: Lu (Letter, Uppercase)
Bidi: L (Left-to-Right)
Decomposition: 0041 0300



You can specify a range of characters as arguments, unicode will show
these characters in nice tabular format, aligned to 256-byte boundaries.  
Use two dots ".." to indicate the range, e.g.

       unicode 0450..0520

will display the whole cyrillic, armenian and hebrew blocks (characters from U+0400 to U+05FF)

       unicode 0400..

will display just characters from U+0400 up to U+04FF

Use --fromcp to query codepoints from other encodings:

$ unicode --fromcp cp1250 -d 200
U+010C LATIN CAPITAL LETTER C WITH CARON
UTF-8: c4 8c  UTF-16BE: 010c  Decimal: &#268;
Č (Č)
Uppercase: U+010C
Category: Lu (Letter, Uppercase)
Bidi: L (Left-to-Right)
Decomposition: 0043 030C

Multibyte encodings are supported:
$ unicode --fromcp big5 -x aff3

and multi-char strings are supported, too:

$ unicode --fromcp utf-8 -x c599c3adc5a5


On format (--format='...'):

Format string tells unicode which information should be displayed.
There is one (and only one) escape character recognised, \n for a new line.

You can use standard python .format() syntax. Following variables are
recognized:

{black} {red} {green} {yellow}
{blue} {magenta} {cyan} {white}  -- ANSI colours (foreground)

{on_black} {on_red} ...          -- ANSI colours (background)

{no_colour} {default} {bold}
{underline} {blink} {reverse}
{concealed}                      -- self-explaining ANSI escape codes

{ordc} -- unicode codepoint of the character (integer)
{name} -- unicode name of the character
{utf8} -- utf8 representation of the character (hexadecimal)
{utf16be} -- utf16 representation of the character (hexadecimal)
{decimal} -- decimal representation of the character
{opt_additional} -- optional representation in additional charset (-c); 
                    empty string if not specified
{pchar} -- the character itself
{opt_flipcase} -- upper- or lowercase opposite of the character, in parentheses;
                  empty if character is not cased
{opt_uppercase}{opt_lowercase} -- optional string describing uppercase
                                  or lowercase variant of the character;
                                  empty if character is not cased
{category} {category_desc} -- character category and its human readable description
{opt_numeric}{numeric_desc} -- the string `Numeric value:' and the numeric value
                               of the character; both empty if the character
                               has no numeric value
{opt_digit}{digit_desc} -- the string `Digit value:' and the digit value
                           of the character; both empty if the character
                           has no digit value
{opt_bidi}{bidi}{bidi_desc} -- the string `Bidi:', the bidi property and
                               a human readable description 
                               of the bidi property; empty if the character
                               has no bidi category
{mirrored_desc} -- the string 'Character is mirrored' if the character is mirrored,
                   empty otherwise
{opt_combining}{combining_desc} -- the string `Combining: ', combining class and a
                                   human readable description of the combining class;
                                   empty if the character is not combining
{opt_decomp}{decomp_desc} -- the string `Decomposition: ' and a hexadecimal sequence
                             of decomposition characters; empty if the character
                             has no decomposition
{opt_unicode_block}{opt_unicode_block_desc} -- the string `Unicode block:',
                                               range of the unicode block
                                               and description of said unicode
                                               block for the given character
{opt_eaw}{eaw_desc} -- the string `East Asian width:' and the human readable
                       value of East Asian width
{opt_derivedage}{opt_derivedage_age}{opt_derivedage_desc} -- the string `Age:',
    the Unicode version the character has been introduced in, and the human
    readable description of the version and the year it has been introduced.

