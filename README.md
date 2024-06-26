# libtermcolor

> [!NOTE]
> This library is archived and simply a record of code I wrote years ago. It is not intended for use nor as a reflection of my skill as a programmer. 

`libtermcolor` allows you to add flair to your messages with colors, italics and other graphics. Currently it supports:

- Foreground and background
- Italics and bold
- Strikethrough, underline and blinking

Documentation is provided through comments in [the header file](include/termcolor.h). See [`use.md`](doc/use.md) for more information.

The main API provided is through these three functions:

```c
int tcol_fprintf(FILE* stream, const char* fmt, ...);
int tcol_printf(const char* fmt, ...);
```

`tcol_printf` behaves the same as `tcol_fprintf` except that `stream` is by default the standard output.

These functions are exactly the same as normal printf except that you can specify colors within brackets. You can escape left brackets with `{{`.

The color is specified within a left and right bracket. There can be as many spaces as you want, but other than that it must only contain valid character sequences. [`use.md`](doc/use.md) explains these sequences in full.

The following code displays `"Hello, world!"` in rainbow colors, all bold:

```c
int result = tcol_printf("{+}{R}H{G}e{Y}l{C}l{M}o{W}, {G}w{C}o{R}r{B}l{W}d{Y}!{0}\n");
if (result != TermColorErrorNone) {
    printf("error: %s\n", tcol_errorstr(result));
    return 1;
}
```

![Hello world in bold rainbow text](img/hello-world.png)

## Building

Clone and make!

```sh
git clone https://github.com/ethanuppal/libtermcolor
cd libtermcolor
make
```
