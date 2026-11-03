# Crash Team Racing Nitro-Fueled (`0100F9F00C696000`)

Update 1.0.15 (`v983040`), SDK 8.2.0. Beenox's game on Vicarious Visions' / Toys
for Bob's Alchemy engine, on NVN. Modules `main`, `subsdk0` (GLSLC) and `sdk`.
No game-specific rewriter cuts or host rules.

On the Mac: the intro, the license and language screens, the title screen and
races, with sound, at 60 fps (`present_interval display`, below). Played with a
Pro Controller. Not tested on the iPhone.

## What it needs

| Setting | Where | Why |
|---|---|---|
| `present_interval display` | [`game.tsv`](game.tsv) | the game asks for present interval 2 (30 fps) but steps its races by elapsed time: at one frame per display tick a race runs at 60 fps at the same speed as at 30 fps |
| `modules main subsdk0 sdk` | `game.tsv` | `subsdk0` is the game's GLSLC, which `main` calls at run time |
| memory and other keys | `game.tsv` | the provisional profile's guesses, which hold through boot and races |

## Shaders

- 1,947 shaders: 1,933 in the 87 IGZ files of `archives/shaders_nx.pak`, read
  through the Alchemy IGA archive reader
  ([Alchemy IGA archives](../../../docs/reference/shaders.md#alchemy-iga-archives)),
  12 whole GLSLC outputs in `main`, and 2 that the game compiles at run time,
  captured on the Mac.
- The run-time pair is compiled only after the title screen's first button
  press, so the capture boot presses A
  ([A run-time compile that waits for a button press](../../../docs/reference/shaders.md#a-run-time-compile-that-waits-for-a-button-press)).

## Found on this game

- [Alchemy IGA archives](../../../docs/reference/shaders.md#alchemy-iga-archives)
- [A run-time compile that waits for a button press](../../../docs/reference/shaders.md#a-run-time-compile-that-waits-for-a-button-press)
- Several audio renderers: a 32 kHz renderer at boot and a 48 kHz one as the
  intro starts; with only one rendered, the frame loop stopped about 3 s later
  ([audio reference](../../../docs/reference/audio.md)).

## Open

- Not tested on the iPhone, nor its touch layout.
- The memory layout is the provisional guess; it held through the races played.
