# How to Play Audio Through Two Headphones at the Same Time on a Mac

> Double Headphones is a Windows app. **On a Mac you don't need it** — macOS has this
> built in. Here's the free, no-download way to play the same audio through two
> headphones (or a headphone + a speaker) at once.

## The built-in way: a Multi-Output Device

macOS can send one audio stream to several output devices simultaneously using a
**Multi-Output Device**. It's free, already on your Mac, and takes about a minute to set up.

1. Connect both headphones (Bluetooth, wired, or USB) so they appear in your sound settings.
2. Open **Audio MIDI Setup** (press `Cmd + Space`, type "Audio MIDI Setup", hit Enter).
3. Click the **`+`** button at the bottom-left → **Create Multi-Output Device**.
4. In the right-hand list, **tick both** of your headphones.
5. *(Recommended)* Set your primary headphones as the **Master Device** (top of the list),
   and enable **Drift Correction** on the *other* device to reduce sync drift.
6. Right-click the new "Multi-Output Device" → **Use This Device For Sound Output**
   (or pick it under  → System Settings → Sound → Output).

Both headphones now play the same audio. To go back, just switch the output back to your
normal device.

## Honest caveats

macOS gives you the core feature for free, but a Multi-Output Device has rough edges:

- **The keyboard volume keys stop working** while a Multi-Output Device is selected.
  Adjust each headphone's volume individually inside Audio MIDI Setup, or on the headphones themselves.
- **Bluetooth sync can drift** between two wireless headphones. "Drift Correction" helps;
  a wired + Bluetooth combination is the most reliable.
- **No per-app control** — it routes all system audio, same as on Windows.

If the volume-key limitation bothers you, third-party Mac tools (e.g. Background Music,
or paid apps like Loopback / SoundSource) add nicer controls — but for "two headphones,
one movie," the built-in Multi-Output Device is usually all you need.

## On Windows instead?

Windows does **not** have a clean built-in equivalent, which is exactly why
**[Double Headphones](https://github.com/maayaranai/double-headphones)** exists — it's a
free one-click app that does on Windows what Multi-Output Device does on Mac.
[Download it here.](https://github.com/maayaranai/double-headphones/releases/latest)
