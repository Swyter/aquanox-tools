# aquanox-tools
Some lightweight reverse-engineering of the first AquaNox's file formats to find out how it works.

The `.bt` opens and decrypts `.pak` files (and their filenames and sizes) as a 010 Editor binary template, and the `.1sc` is a fully-fledged extractor.

# Internal game formats
* `.dds`, `.tga`: Generic texture and image formats. _DirectDraw Surfaces_ are generally compressed with DXT formats, _Targa_ files seem uncompressed.
* `.sco`: Some kind of precompiled Lua bytecode. The extension probably stands for _script object_, they probably did this to obfuscate it, but variables and symbols can probably be recovered from there without much fuss.
* `.des`: Some kind of serialized configuration/description file. Files like `ini\control_menu.des` in `aquanox.6.pak` are text-based and human readable. A lot of game text is stored in there. I think the `~` signals that the file has been cooked as binary.
* `.fog`: Some kind of look-up table and sets the color of the volumetric fog based on distance and depth, maybe created from the `fog.tga`.
* `.msb`: The main mesh file format, from the look of it.
