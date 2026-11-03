# openjkdf2-star-wars-episode-i-ii-iii
## OpenJKDF2 - Star Wars Episode I-II-III Remake
A remake of *Star Wars Episode I-II-III* rebuilt in the Jedi Knight Dark Forces II decompilation project.

## Github Treeview
[https://treegit.macosxjs.com/?url=igiteam/openjkdf2-star-wars-episode-i-ii-iii
](https://treegit.macosxjs.com/?url=igiteam/openjkdf2-star-wars-episode-i-ii-iii)

## Github Tree Api Direct JSON
[https://api.github.com/repos/igiteam/openjkdf2-star-wars-episode-i-ii-iii/git/trees/main?recursive=1
](https://api.github.com/repos/igiteam/openjkdf2-star-wars-episode-i-ii-iii/git/trees/main?recursive=1)

## Reference Links
[https://www.massassi.net/](https://www.massassi.net/)

[https://www.massassi.net/programs/](https://www.massassi.net/programs/)

[https://www.massassi.net/programs/jed/ZED_2008-01-31.zip](https://www.massassi.net/programs/jed/ZED_2008-01-31.zip)

[https://www.massassi.net/3dos/jk.html](https://www.massassi.net/3dos/jk.html)

[![ZED Editor Tutorials](https://img.youtube.com/vi/8DoHek4jti4/maxresdefault.jpg)](https://www.youtube.com/playlist?list=PLb8oNKiUbnjEug75t5V8XUR26jmoyjEvs)


![MacOS Screenshot](docs/images/screenshot.png)

## [Latest Releases](https://github.com/shinyquagsire23/OpenJKDF2/releases) | [Report a crash or bug](https://github.com/shinyquagsire23/OpenJKDF2/issues)

OpenJKDF2 is a function-by-function reimplementation of DF2 in C, with 64-bit ports to Windows 7+, macOS 10.15+, and Linux. Files are organized as closely to the original game as possible, based on symbols from the Grim Fandango Remaster Android/Linux/macOS port, as well as scattered assertions from various other games. It also contains the original versions of `byacc` and `flex` used for COG script parsing.

OpenJKDF2 does *not* include any original game assets; a valid copy of JKDF2 is *required* and can be purchased from [GOG](https://www.gog.com/game/star_wars_jedi_knight_dark_forces_ii) or [Steam](https://store.steampowered.com/app/32380/STAR_WARS_Jedi_Knight_Dark_Forces_II/). The GOG version is recommended, since it is DRM-free and also includes the soundtrack in Ogg Vorbis format. If you'd like to try before you buy, a WebAssembly demo of OpenJKDF2 can be found at https://maxthomas.dev/openjkdf2/.

Support for playing the original soundtrack from Ogg Vorbis files is primarily supported for the GOG and Steam versions of the game assets. Original disk soundtracks can also be loaded from `MUSIC/1/Track<2..8>.ogg` and `MUSIC/2/Track<2..12>.ogg` for each disk's soundtrack. If files are missing, it will instead attempt to use a GOG track number from `MUSIC/Track<12..32>.ogg`. Dumping the soundtrack from disks at install time is planned for a future release of OpenJKDF2, but is not currently implemented.

## Platforms
OpenJKDF2 supports the following configurations:

| Configuration | Renderer | Description |
| --- | --- | --- |
| 64-bit Windows/SDL2 | OpenGL 3.3 | 64-bit Windows compilation with SDL2 and OpenAL. DirectX dependencies are replaced with SDL2 and OpenAL. |
| MacOS x86_64/AArch64 | OpenGL 3.3 | 64-bit MacOS compilation with SDL2 and OpenAL. All release packages include both Intel and ARM64. |
| 64-bit Linux/SDL2 | OpenGL 3.3 | 64-bit Linux compilation with SDL2 and OpenAL. |
| Emscripten/WebAssembly | WebGL 2/OpenGL ES 3 | WebAssembly with SDL2 and OpenAL. Runs in a web browser. Since WASM only supports 32-bit pointers, this will likely be less buggy than 64-bit, but less performant. |
| x86 Linux/SDL2, mmap blobs | OpenGL 3.3 | 32-bit Linux compilation with SDL2 and OpenAL. JK.EXE is memory mapped into the process and used as a "binary blob"; Unimplemented functions will fall back to JK.EXE implementations. |
| 32-bit Linux/SDL2, blobless | OpenGL 3.3 | 32-bit Linux compilation with SDL2 and OpenAL. The output executable is a swap-in replacement for JK.EXE, but will be missing functions and will crash on reaching unimplemented code. |
| x86 Win32/MinGW DLL | Software/DirectX | Win32 hooked build, JK.EXE is patched to load `df2_reimpl.dll` execute `hook_init_win` before JK.EXE's `main` function. Unimplemented functions will fall back to JK.EXE implementations. `df2_reimpl_kvm.dll` is used for the KVM target |

The following implementations are in-progress or planned:

| Configuration | Renderer | Description | Status |
| --- | --- | --- | --- |
| Android | OpenGL ES 3 | Not a huge priority, but would be nice to have. | It compiles and renders! Input/menuing is lacking. |
| iOS | Metal? | Not a huge priority, but would be nice to have. | Not started |
| Switch libnx | OpenGL ES 3 | Not a huge priority, but would be nice to have. | Not started |
| 32-bit Windows/SDL2 | OpenGL 3.3 | Windows compilation with SDL2 and OpenAL. DirectX dependencies are replaced with SDL2 and OpenAL. Targeting Windows XP ~ Windows 7 | Not started |
| 32-bit Windows/DirectX | Direct3D 3 | Faithful decompilation with original DirectX bindings/renderer. | Not started |

Linux building works on AArch64/RPi4 with llvmpipe, but V3D GLES has trouble with palettes.

OpenJKDF2 requires game data from a licensed copy of Jedi Knight: Dark Forces II in order to run; No game assets are provided by OpenJKDF2. On Linux, paths and filenames may be case-sensitive. Your directory structure should look something like this:
```
.
├── JK.EXE
├── MUSIC
│   ├── Track12.ogg
│   ├── Track13.ogg
│   ├── Track14.ogg
│   ├── Track15.ogg
│   ├── Track16.ogg
│   ├── Track17.ogg
│   ├── Track18.ogg
│   ├── Track22.ogg
│   ├── Track23.ogg
│   ├── Track24.ogg
│   ├── Track25.ogg
│   ├── Track26.ogg
│   ├── Track27.ogg
│   ├── Track28.ogg
│   ├── Track29.ogg
│   ├── Track30.ogg
│   ├── Track31.ogg
│   └── Track32.ogg
├── episode
│   ├── JK1.gob
│   ├── JK1CTF.gob
│   └── JK1MP.gob
├── openjkdf2-64
├── player
└── resource
    ├── Res1hi.gob
    ├── Res2.gob
    ├── jk_.cd
    └── video
        ├── 01-02A.SMK
        ├── 03-04A.SMK
        ├── 06A.SMK
        ├── 08-10A.SMK
        ├── 12A.SMK
        ├── 16A.SMK
        ├── 18-19A.SMK
        ├── 21A.SMK
        ├── 23A.SMK
        ├── 25A.SMK
        ├── 27A.SMK
        ├── 33-34A.SMK
        ├── 36A.SMK
        ├── 38A.SMK
        ├── 39A.SMK
        ├── 41-42A.SMK
        ├── 41DA.SMK
        ├── 41DSA.SMK
        ├── 44A.SMK
        ├── 46A.SMK
        ├── 48A.SMK
        ├── 50A.SMK
        ├── 52-53A.SMK
        ├── 54A.SMK
        └── 57A.SMK
```

## Building

See [here](BUILDING.md) for instructions.

## Contributing

Contributions in the form of code cleanup and documentation are highly welcomed. See [CONTRIBUTING.md](CONTRIBUTING.md) for details on what kinds of cleanup tasks still need to be done. OpenJKDF2 is not currently accepting monetary donations, however [detailed bug and crash reports](https://github.com/shinyquagsire23/OpenJKDF2/issues) are always appreciated, including bugs/crashes involving mods.

## TL;DR: What Isn't Implemented, Yet
 - Load Configuration and Save Configuration in Setup > Controls > Options
 - Using plus or minus to resize the screen (with SDL2, resolution auto-resizes to window size)

## Usage with original JK.EXE and DirectX using hooks
See [here](HOOKS.md) for instructions.

## Methodology
The bulk of research and documentation occurs in IDA. Every function has been identified to a file prefix (ie `stdHashTable_`) with a corresponding .c/.h file. RenderDroid (`rd*`) and LEC stdlib (`std*`) functions are 90% canonically named, based on symbols from Grim Fandango Remastered.

Reverse engineering is a parallel effort between structure documentation and function identification. Once structures are sufficiently documented, Hex-Rays can be used for decompilation. While most Hex-Rays output works outright, many loops and structures require manual intervention. Output is generally cleaned and tidied to remove redunant stack variables or too-deep nesting. `sizeof` and obvious inlining and macros should also be adjusted as appropriate.

Engine variables and yet-to-be-decompiled functions are referenced using `define` macros and static function pointers, respectively. Once a file is decompiled enough that an engine variable is no longer referenced by non-decompiled code, the variables can be declared in their respective C files. For decompiled functions which are only referenced by non-decompiled functions, a `hook_function` call is added in `main.c` to redirect code execution to `df2_reimpl.dll` from `JK.EXE`.

Progress is tracked using `analyze.py`, `output.map` and `ida_copypaste_funclist_nostdlib.txt`: After compiling `df2_reimpl.dll`, symbols can be compared against the `.idb` to determine how much of the original `.text` is actually in use, and how much has been hooked and replaced.

If you'd like a copy of my IDB to examine functions which haven't been decompiled yet (or for any other use), let me know.

## Current Progress

Generated using `analyze.py`. Some filenames may be inaccurate or incomplete (see `ida_copypaste_funclist_nostdlib.txt` for a full function name listing).

```

[file]                         [size]     [% of text]   [% complete]  [decomp / total] 
DirectX                        0x1e       0.003%        100.000%        5 / 5          
jkGob                          0x29       0.004%        100.000%        2 / 2          
jkGuiDecision                  0x45       0.006%        100.000%        3 / 3          
sithStrTable                   0x5b       0.008%        100.000%        4 / 4          
sithCopyright                  0x67       0.010%        100.000%        1 / 1          
jkStrings                      0x89       0.013%        100.000%        5 / 5          
jkGuiGeneral                   0xc5       0.018%        100.000%        3 / 3          
jkSmack                        0xee       0.022%        100.000%        4 / 4          
rdFace                         0xf6       0.023%        100.000%        4 / 4          
jkGuiControlOptions            0x105      0.024%        100.000%        3 / 3          
stdHashKey                     0x107      0.024%        100.000%       10 / 10         
rdCanvas                       0x113      0.025%        100.000%        4 / 4          
jkGuiEsc                       0x18f      0.037%        100.000%        3 / 3          
rdroid                         0x1f6      0.047%        100.000%       27 / 27         
sithHeader                     0x1f9      0.047%        100.000%        1 / 1          
sithTime                       0x213      0.049%        100.000%        6 / 6          
jkGuiSingleTally               0x21b      0.050%        100.000%        4 / 4          
jkGuiSetup                     0x240      0.053%        100.000%        4 / 4          
jkGuiSound                     0x274      0.058%        100.000%        3 / 3          
sithItem                       0x275      0.058%        100.000%        5 / 5          
jkGuiGameplay                  0x2b2      0.064%        100.000%        3 / 3          
stdMemory                      0x2ba      0.065%        100.000%        7 / 7          
sithEvent                      0x2e3      0.069%        100.000%        9 / 9          
stdMci                         0x2ef      0.070%        100.000%        7 / 7          
jkGuiObjectives                0x308      0.072%        100.000%        4 / 4          
jkControl                      0x331      0.076%        100.000%        4 / 4          
Windows                        0x39a      0.085%        100.000%       11 / 11         
stdString                      0x3b3      0.088%        100.000%       11 / 11         
sithRenderSky                  0x3c2      0.089%        100.000%        5 / 5          
jkGuiDialog                    0x3e0      0.092%        100.000%        6 / 6          
sithModel                      0x3f1      0.094%        100.000%        8 / 8          
rdThing                        0x42f      0.099%        100.000%       12 / 12         
stdGdi                         0x430      0.099%        100.000%       10 / 10         
jkCutscene                     0x443      0.101%        100.000%        7 / 7          
sithKeyFrame                   0x44e      0.102%        100.000%        5 / 5          
stdPcx                         0x45e      0.104%        100.000%        2 / 2          
sithDSSCog                     0x460      0.104%        100.000%        4 / 4          
smack                          0x466      0.104%        100.000%        6 / 6          
sithPlayerActions              0x46f      0.105%        100.000%        3 / 3          
rdMath                         0x47d      0.107%        100.000%        6 / 6          
rdLight                        0x49f      0.110%        100.000%        8 / 8          
jkGuiMain                      0x4b1      0.111%        100.000%        6 / 6          
stdFnames                      0x4ee      0.117%        100.000%       14 / 14         
sithSprite                     0x4f1      0.117%        100.000%        6 / 6          
jkGui                          0x4fb      0.118%        100.000%       10 / 10         
jkGuiTitle                     0x4fb      0.118%        100.000%       10 / 10         
sithMaterial                   0x4fd      0.118%        100.000%        9 / 9          
wuRegistry                     0x5b2      0.135%        100.000%       12 / 12         
stdHashTable                   0x5d6      0.138%        100.000%       10 / 10         
Video                          0x5dc      0.139%        100.000%        5 / 5          
sithConsole                    0x5de      0.139%        100.000%       13 / 13         
sithExplosion                  0x61d      0.145%        100.000%        4 / 4          
sithAIClass                    0x689      0.155%        100.000%        7 / 7          
rdPrimit2                      0x69a      0.157%        100.000%        5 / 5          
sithCogScript                  0x6ca      0.161%        100.000%        9 / 9          
Window                         0x6db      0.163%        100.000%       13 / 13         
stdGob                         0x6dd      0.163%        100.000%       14 / 14         
jkAI                           0x6e7      0.164%        100.000%        5 / 5          
sithMain                       0x72b      0.170%        100.000%       16 / 16         
jkGuiControlSaveLoad           0x732      0.171%        100.000%        6 / 6          
jkGuiPlayer                    0x73a      0.171%        100.000%        5 / 5          
rdSprite                       0x76d      0.176%        100.000%        5 / 5          
stdConffile                    0x78d      0.179%        100.000%       13 / 13         
jkGuiMap                       0x793      0.180%        100.000%        8 / 8          
sithTemplate                   0x79d      0.181%        100.000%       10 / 10         
sithParticle                   0x7f5      0.189%        100.000%       10 / 10         
sithSector                     0x806      0.190%        100.000%       13 / 13         
sithComm                       0x80b      0.191%        100.000%       11 / 11         
sithMap                        0x814      0.192%        100.000%        6 / 6          
Main                           0x87b      0.201%        100.000%        4 / 4          
jkGuiMultiTally                0x8aa      0.206%        100.000%        7 / 7          
jkGuiSingleplayer              0x8d8      0.210%        100.000%        7 / 7          
jkCredits                      0x8e4      0.211%        100.000%        6 / 6          
sithCogFunctionSector          0x93a      0.219%        100.000%       22 / 22         
sithCogFunctionAI              0x943      0.220%        100.000%       20 / 20         
stdSound                       0x9bf      0.231%        100.000%       27 / 27         
sithGamesave                   0x9bf      0.231%        100.000%        7 / 7          
jkGuiForce                     0x9dd      0.234%        100.000%       11 / 11         
sithSound                      0xa00      0.237%        100.000%       13 / 13         
rdParticle                     0xa0d      0.239%        100.000%       10 / 10         
rdMaterial                     0xa2d      0.241%        100.000%        9 / 9          
sithSoundClass                 0xa46      0.244%        100.000%       16 / 16         
sithCogFunctionSound           0xa97      0.251%        100.000%       14 / 14         
rdKeyframe                     0xa99      0.251%        100.000%        8 / 8          
rdCamera                       0xaa8      0.253%        100.000%       26 / 26         
jkGuiSaveLoad                  0xb21      0.264%        100.000%        9 / 9          
rdPolyLine                     0xb42      0.267%        100.000%        6 / 6          
jkSaber                        0xb54      0.269%        100.000%        8 / 8          
jkGuiKeyboard                  0xb57      0.269%        100.000%       14 / 14         
jkGuiNetHost                   0xbc6      0.279%        100.000%        6 / 6          
sithOverlayMap                 0xbf8      0.284%        100.000%        9 / 9          
rdVector                       0xd29      0.312%        100.000%       55 / 55         
jkGuiMouse                     0xdb5      0.325%        100.000%       14 / 14         
DirectDraw                     0xdd4      0.328%        100.000%       16 / 16         
jkEpisode                      0xdd9      0.329%        100.000%       10 / 10         
sithCogFunctionPlayer          0xdf0      0.331%        100.000%       42 / 42         
jkHudInv                       0xe43      0.338%        100.000%        9 / 9          
sithCogFunctionSurface         0xe92      0.346%        100.000%       38 / 38         
sithActor                      0xf9c      0.370%        100.000%       13 / 13         
stdConsole                     0xfff      0.380%        100.000%       20 / 20         
jkGuiMultiplayer               0x1097     0.394%        100.000%       13 / 13         
DirectPlay                     0x10cc     0.399%        100.000%       31 / 31         
VBuffer                        0x10dc     0.400%        100.000%        4 / 4          
jkCog                          0x11b8     0.420%        100.000%       40 / 40         
stdControl                     0x11ec     0.425%        100.000%       22 / 22         
sithPuppet                     0x1222     0.430%        100.000%       17 / 17         
sithCamera                     0x124b     0.434%        100.000%       23 / 23         
jkGuiDisplay                   0x12ff     0.451%        100.000%       11 / 11         
jkGuiJoystick                  0x13f0     0.473%        100.000%       19 / 19         
jkDSS                          0x13f6     0.474%        100.000%       32 / 32         
sithCogYACC                    0x152b     0.502%        100.000%       10 / 10         
jkRes                          0x15b6     0.515%        100.000%       23 / 23         
jkMain                         0x16cd     0.541%        100.000%       53 / 53         
sithWorld                      0x1718     0.548%        100.000%       22 / 22         
sithDSS                        0x175d     0.554%        100.000%       22 / 22         
stdMath                        0x182a     0.573%        100.000%       23 / 23         
rdActive                       0x1a55     0.625%        100.000%        8 / 8          
sithCogExec                    0x1aec     0.639%        100.000%       31 / 31         
sithCogParse                   0x1b2a     0.645%        100.000%       26 / 26         
jkHud                          0x1c9b     0.679%        100.000%       17 / 17         
jkDev                          0x1fd6     0.755%        100.000%       41 / 41         
sithInventory                  0x2150     0.791%        100.000%       62 / 62         
sithDSSThing                   0x22aa     0.823%        100.000%       37 / 37         
sithRender                     0x23de     0.851%        100.000%       22 / 22         
jkGuiBuildMulti                0x258b     0.891%        100.000%       24 / 24         
sithSoundMixer                 0x2626     0.905%        100.000%       37 / 37         
stdDisplay                     0x267b     0.913%        100.000%       37 / 37         
sithCogFunction                0x26c2     0.920%        100.000%      119 / 119        
sithAI                         0x2771     0.936%        100.000%       35 / 35         
rdModel3                       0x2a7e     1.008%        100.000%       23 / 23         
std3D                          0x2c4a     1.051%        100.000%       39 / 39         
rdMatrix                       0x2c85     1.056%        100.000%       56 / 56         
sithAICmd                      0x2cc0     1.062%        100.000%       22 / 22         
jkGuiRend                      0x2cd7     1.064%        100.000%       68 / 68         
jkPlayer                       0x2da2     1.083%        100.000%       45 / 45         
sithPhysics                    0x310b     1.164%        100.000%       13 / 13         
sithWeapon                     0x32a8     1.202%        100.000%       33 / 33         
rdCache                        0x331c     1.213%        100.000%       16 / 16         
sithCogFunctionThing           0x3a4c     1.383%        100.000%      142 / 142        
rdClip                         0x81f2     3.084%        100.000%       17 / 17         
sithAIAwareness                0x31f      0.074%        90.488%         5 / 6          
stdComm                        0x53c      0.124%        98.955%        16 / 17         
stdFileUtil                    0x687      0.155%        54.159%         6 / 11         
stdBmp                         0x6b8      0.159%        0.000%          0 / 3          
sithAnimClass                  0x6cc      0.161%        94.080%         4 / 5          
stdStrTable                    0x7b6      0.183%        82.877%         4 / 6          
stdColor                       0x97e      0.225%        24.198%         3 / 11         
jkGame                         0x98f      0.227%        80.384%        12 / 13         
stdPalEffects                  0xa66      0.247%        85.875%        16 / 21         
stdLbm                         0xc24      0.288%        0.000%          0 / 3          
rdColormap                     0xcf4      0.307%        47.738%         7 / 12         
stdPlatform                    0xdde      0.329%        49.042%        37 / 43         
sithPlayer                     0xe72      0.343%        95.944%        23 / 27         
stdBitmap                      0xeb6      0.349%        47.398%         6 / 14         
sithTrackThing                 0xf9f      0.371%        90.098%        12 / 15         
rdPuppet                       0x101f     0.383%        97.407%        15 / 19         
stdGif                         0x1162     0.412%        0.000%          0 / 4          
sithCommand                    0x11b2     0.420%        91.545%        18 / 20         
sithIntersect                  0x12a8     0.443%        92.588%         9 / 12         
rdPrimit3                      0x16e0     0.543%        91.684%         7 / 9          
stdFont                        0x181a     0.572%        75.284%        12 / 20         
sithSurface                    0x1c6a     0.674%        96.838%        33 / 35         
sithCog                        0x1ed3     0.731%        90.686%        21 / 28         
sithMulti                      0x252a     0.882%        91.423%        29 / 35         
sithCollision                  0x2827     0.953%        91.954%        19 / 22         
sithControl                    0x285a     0.958%        99.613%        31 / 33         
sithThing                      0x338c     1.223%        86.829%        43 / 49         
rdRaster                       0xf04d     5.702%        0.195%          1 / 89         
rdZRaster                      0x15fb4    8.346%        0.000%          0 / 73         
rdAFRaster                     0x1620d    8.402%        0.000%          0 / 122        
rdNRaster                      0x304d4    18.339%       0.000%          0 / 87         
---------------------------------------------------------------------------------

Total completion:
-----------------
56.758% by weight
95.857% by weight excluding rasterizer
2694 / 3169 functions
2694 / 2798 functions excluding rasterizer

Subsystem Breakdown (Not Decomp'd)
----------------------------------
[subsys]       [% of text]  [TODO / total]
sith           0.542%           40 / 1319
stdPlatform    0.168%            6 / 43
std            1.494%           47 / 376
jkGui          0.000%            0 / 284
rd             0.216%           11 / 345
jk             0.044%            1 / 324
Raster         40.778%         370 / 371
other          0.000%            0 / 107
-----------------------------------------
total          43.242%         475 / 3169

Subsystem Breakdown (Not Decomp'd, Excl Raster)
-----------------------------------------------
[subsys]       [% of text]  [TODO / total]
sith           0.916%           40 / 1319
stdPlatform    0.283%            6 / 43
std            2.524%           47 / 376
jkGui          0.000%            0 / 284
rd             0.364%           11 / 345
jk             0.075%            1 / 324
other          0.000%            0 / 107
-----------------------------------------
total          4.162%          105 / 2798

```

## Dev Environment

**Official White Wii Remote With Nunchuk — Tested And Working — £14.99**
[https://www.ebay.co.uk/itm/800847189353](https://www.ebay.co.uk/itm/800847189353)

**Infrared Sensor Bar USB for Wii Emulator Remote Motion Detection Setup — £6.69**
[https://www.ebay.co.uk/itm/227423830875](https://www.ebay.co.uk/itm/227423830875)

**Apple MacBook Pro Retina 15in (2014) i7 2.8GHz 16GB 1TB SSD GT 750M — £120.30**
[https://www.ebay.co.uk/itm/800844561513](https://www.ebay.co.uk/itm/800844561513)

**WS11WineCX20.0.4 (Wine engine)**
[https://igiteam.github.io/wine_engines/](https://igiteam.github.io/wine_engines/)

**Official Genuine Sony PS3 PlayStation 3 DualShock 3 Wireless Controller Black — £19.99**
[https://www.ebay.co.uk/itm/840031043465](https://www.ebay.co.uk/itm/840031043465)

**Amazon Basics 4K HDMI Cable 3m — 18Gbps High Speed with Ethernet, 4K@60Hz, 2160p — £8.44**
[https://www.ebay.co.uk/itm/327352257557](https://www.ebay.co.uk/itm/327352257557)

**wiimote_nunchuk_macosx**
[https://github.com/igiteam/wiimote-nunchuk](https://github.com/igiteam/wiimote-nunchuk)

**xbox360_input_gui_py**
[https://github.com/igiteam/xbox360_input_gui_py](https://github.com/igiteam/xbox360_input_gui_py)

**logitec_mx_mouse_3_macos**
[https://github.com/igiteam/logitec_mx_mouse_3_macos](https://github.com/igiteam/logitec_mx_mouse_3_macos)

**igi1-macbook-3d-workstation**
[https://github.com/igiteam/igi1-macbook-3d-workstation](https://github.com/igiteam/igi1-macbook-3d-workstation)

---

# OpenPhantom: Star Wars Episode I, The Phantom Menace PC fixes and modding tools
[https://github.com/igiteam/OpenPhantom](https://github.com/igiteam/OpenPhantom)

[![Latest Release](https://img.shields.io/github/v/release/OpenPhantom/OpenPhantom?style=for-the-badge&label=Latest-Release)](https://github.com/OpenPhantom/OpenPhantom/releases/latest)
[![All Downloads](https://img.shields.io/github/downloads/OpenPhantom/OpenPhantom/total?style=for-the-badge&label=Downloads)](https://github.com/OpenPhantom/OpenPhantom/releases)
[![GitHub Stars](https://img.shields.io/github/stars/OpenPhantom/OpenPhantom?style=for-the-badge&label=Stars)](https://github.com/OpenPhantom/OpenPhantom/stargazers)
[![License](https://img.shields.io/github/license/OpenPhantom/OpenPhantom?style=for-the-badge)](https://github.com/OpenPhantom/OpenPhantom/blob/main/LICENSE)

OpenPhantom is a PC fix and modding project for Star Wars Episode I: The Phantom Menace (1999). It gets the original PC game running on Windows 10 and Windows 11, and on Linux and Steam Deck through Proton, with a modern installer that works from your original CD, widescreen and ultrawide resolutions, uncapped FPS, a corrected field of view, mouse look, and working music and video. Alongside the fixes, OpenPhantom reverse engineers and reconstructs the game's engine as documented, maintainable source code, with tools for modding, editing and extending the game.

**[Download the latest release](https://github.com/OpenPhantom/OpenPhantom/releases/latest)** · [Installation guide](https://github.com/OpenPhantom/OpenPhantom/wiki/Installation-Guide) · [Discord](https://discord.gg/73UbZN2y7x) · [Website](https://swopenphantom.org/)

The project has two parts. The legacy patches are useful today: they modify the retail executable in memory so the game you already own runs with modern fixes. The reconstructed engine is the long-term work: rebuilding the game's systems from the ground up as clean source code that can support deeper modding and new features.

<img width="1920" height="400" alt="Star Wars Episode I: The Phantom Menace running at ultrawide resolution with OpenPhantom." src="https://github.com/user-attachments/assets/ad9cd6fb-8bcd-4b25-8d0a-65e221888bfc" />

*Ultra-wide support with OpenPhantom.*
[![Ultra-wide support with OpenPhantom](https://raw.githubusercontent.com/igiteam/OpenPhantom/refs/heads/main/openphantom-1.png)](https://raw.githubusercontent.com/igiteam/OpenPhantom/refs/heads/main/openphantom-1.png)

*4K rendering with expanded draw distance.*
[![4K rendering with expanded draw distance](https://raw.githubusercontent.com/igiteam/OpenPhantom/refs/heads/main/openphantom-2.png)](https://raw.githubusercontent.com/igiteam/OpenPhantom/refs/heads/main/openphantom-2.png)

*Free Camera/ No Clip/ Photo mode.*
[![Free Camera](https://raw.githubusercontent.com/igiteam/OpenPhantom/refs/heads/main/openphantom-3.png)](https://raw.githubusercontent.com/igiteam/OpenPhantom/refs/heads/main/openphantom-3.png)

**Want to play?** Download the [latest release](https://github.com/OpenPhantom/OpenPhantom/releases/latest) and run the OpenPhantom installer. It installs the original game from your own disc and applies the available patches and fixes for modern Windows PCs. You don't need to build anything from source.

## What's Included  

| | |
|---|---|
| [`installer/`](installer/) | **Working** A wizard that installs the game from your own disc and then the parts of the patch you tick. It carries no game data; the disc is read on your machine. Everything it installs is inside the installer and nothing is downloaded. See its [README](installer/README.md) |
| [`legacy/`](legacy/) | **Working**  Fixes that patch the original 1999 executable in memory: field of view, resolutions, frame rate, mouse look, music, decals and more. A loader and one DLL per feature, built with CMake. See its [README](legacy/README.md) |
| `engine/` | The reimplementation. Not started |
| `editor/` | Tools for maps, assets and game content. Not started |
| `architecture/` | How the original engine is put together, written down. Not started |

## Version numbers

The patch and the installer have **two separate version numbers**. They always did, apart from one
release.

| | numbering | tags |
|---|---|---|
| the patch, `legacy/` | `0.4.x` | `v0.4.0`, `v0.4.1`, ... |
| the installer that carries it | `1.4.x` | `i1.4`, `i1.4.1`, ... |

The last digit moves together on a release. The DLLs carry the **patch** number, so a DLL's
properties and the first line of `engine_fixes.log` say `0.4.3` while the installer that delivered
them says `1.4.3`.

**One release merged the two into a single number**, published as `v1.5.0` and `i1.5.0`. That's
been undone. On GitHub that release is now **`v0.4.1` and `i1.4.1`**, and the one after it is
`v0.4.2` and `i1.4.2`.

**Only the release name changed; nothing was rebuilt.** The installer in that release still reports
`1.5.0` in its properties and in Add and Remove Programs, because it's the same file. If you have it
installed, that's why the number doesn't match the release name.

The installer doesn't compare version numbers. It finds an existing installation by its
application id and asks what you want to do with it.

## Documentation

Full guides for installation, usage and configuration are in the
[wiki](https://github.com/OpenPhantom/OpenPhantom/wiki):

* [Installation Guide](https://github.com/OpenPhantom/OpenPhantom/wiki/Installation-Guide)
* [Currently working on, with spoilers](https://github.com/OpenPhantom/OpenPhantom/wiki/Currently-Working-On-Spoilers)
* [Known Issues](https://github.com/OpenPhantom/OpenPhantom/wiki/Known-Issues)
* [Reporting Issues with the OpenPhantom Patches](https://github.com/OpenPhantom/OpenPhantom/wiki/Issues)

## Goals

* Reconstruct the original engine as clean, maintainable source code.
* Keep the original gameplay. If the 1999 look or feel was intended, it stays.
* Run on modern systems, including Linux and 64 bit builds.
* Improve stability, performance and extensibility without changing how the game plays.
* Provide real tools for editing maps, assets and content.
* Support community modding, and stay open to contributions.

## Getting involved

This is a community project. Code, documentation, tests, tooling, research notes and good bug
reports are all welcome, and you don't need to know the engine to start.

[`CONTRIBUTING.md`](CONTRIBUTING.md) has how we work: how to report something usefully, what a
pull request needs, and the ground rules for working against a binary you do not have the source
to. Each component adds its own rules on top; `legacy/CONTRIBUTING.md` is the one that exists so
far.

The most useful thing right now is testing. Every fix has been played in a full installation, and
each one's README says what was checked. But a couple of machines isn't everywhere, so a report of
what happened on yours, with `engine_fixes.log` attached, helps a lot. The log names the build each
fix came from, which is usually the first thing we need to know.

## Discord

The Phantom Discord is where the community talks: players, modders and developers sharing videos,
mods and ideas. As OpenPhantom grows it is also where development updates, custom content and
tools land.

**https://discord.gg/73UbZN2y7x**

## You need your own copy of the game

OpenPhantom ships no game data. No assets, no executables, no extracted files, nothing
proprietary, in the repository or in a release. Everything here operates on files you already own,
and you need a legally obtained copy of *Star Wars Episode I: The Phantom Menace* for PC to use
any of it.

## Legal

An independent fan project. Not affiliated with, endorsed by or sponsored by LucasArts, Lucasfilm
Ltd or Disney. All trademarks, game titles and related intellectual property belong to their
respective owners. OpenPhantom claims no ownership of any original game content and redistributes
none of it.

## Licence

MIT. The source here is free to use, modify and distribute under those terms, provided the licence
notice travels with it. See [LICENSE](LICENSE).

The licence covers this source code only, and not the third-party binaries the installer carries
in `installer/dist/`, which are each under their own terms and include GPL and proprietary
components. See [installer/THIRD-PARTY-NOTICES.md](installer/THIRD-PARTY-NOTICES.md), which also
records what a release has to ship alongside the installer to satisfy them.

It grants nothing regarding the original game, its
assets, or anything else its rights holders own. Release archives may also contain third party
components under their own licences, which are named in the release notes.

## Contact

General enquiries and feedback: **openphantom@proton.me**

For anything technical, open an issue here; more people will see it and it stays searchable.
