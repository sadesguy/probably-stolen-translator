# Probably Stolen: translate mods into Russian

[Русский](README.md) · **English** · [Release 0.4.11](https://github.com/sadesguy/probably-stolen-translator/releases/tag/v0.4.11)

This community mod prepares Russian translations **before you open a save**. Once you have a saved translation pack, play without the AI helper or an internet connection. You only need the helper to generate or update a pack on your own computer.

## 1. Install the game mod

1. Close *Probably Stolen*. In Steam, open the game's **Manage → Browse local files**.
2. Download [Workshop-Mod.zip](https://github.com/sadesguy/probably-stolen-translator/releases/download/v0.4.11/Workshop-Mod.zip). Despite the filename, this is the **manual installation**. Create a folder named `LocalModTranslator` inside the game's `Mods` folder. Put the two extracted files in it:
   ```text
   Mods/LocalModTranslator/
   ├── manifest.xml
   └── LocalModTranslator.dll
   ```
3. Start the game. In **Mods** (`Моды`), select **Локальный переводчик модов**. Activate it (or **Review and enable** if prompted), review its network permission, enable the mods you want translated and restart the game. Select **Русский** as the game language.
4. In the main menu, open the translator's **settings**. If a matching offline pack is already installed, load your save and play. To make one, click **Перевести все моды** (“Translate all mods”). If the helper isn't running, the game shows instructions. **Keep the game open.**

If you install a future Workshop release instead, subscribe, let Steam finish downloading, then follow step 3. Don't install both versions: the local copy takes priority. See the [game developer's activation guide](https://github.com/dragonpan2/probably-stolen-modding/blob/main/ModdingGuide.md#steam-workshop).

## 2. Start the local AI helper

Download **one** file for your computer. Extract the **entire** archive to your own folder **outside Steam**. Do not put the helper in `Mods` or run it from the ZIP preview. The [game's scanner rules](https://github.com/dragonpan2/probably-stolen-modding/blob/main/ModdingGuide.md#capabilities-and-the-scanner) are why the launcher is separate.

| Computer | Get this ZIP | Double-click after extraction |
| --- | --- | --- |
| Windows 10/11 x64, Intel or AMD | [Windows-Local-AI.zip](https://github.com/sadesguy/probably-stolen-translator/releases/download/v0.4.11/Windows-Local-AI.zip) | `helper/Start Translator.cmd` |
| Apple Silicon Mac running the Steam game through Wine | [Mac-Local-AI.zip](https://github.com/sadesguy/probably-stolen-translator/releases/download/v0.4.11/Mac-Local-AI.zip) | `companion/Start Translator.command` in **Finder**, not Wine |

![Illustration: extract your platform ZIP outside Steam, then open Start Translator.cmd inside helper on Windows or Start Translator.command inside companion on Mac.](assets/start-helper.png)

- **Windows:** Use a local NTFS drive. The helper includes Python. It needs a physical Vulkan-capable GPU, its driver, and the [Microsoft Visual C++ v14 x64 runtime](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist).
- **Mac:** The helper uses Metal and needs native ARM64 Python 3.9 or newer. If missing, use the [Python.org macOS installer](https://www.python.org/downloads/macos/). Intel Macs and Rosetta Python are not supported.
- **First run:** Allow about **6 GB of free disk space**, plus enough GPU memory for the model. The helper asks before downloading about **5.2 GB**: [Google's Gemma model](https://huggingface.co/google/gemma-4-E4B-it-qat-q4_0-gguf) and the [llama.cpp engine](https://github.com/ggml-org/llama.cpp/releases/tag/b12477). No need to install them manually. Your dialogue is processed locally, never sent to a cloud translator. To check your ZIP, compare its SHA-256 against the [release checksums](https://github.com/sadesguy/probably-stolen-translator/releases/download/v0.4.11/SHA256SUMS.txt).

## 3. Prepare, then play offline

1. Keep the helper window open. Wait for **Ready** on Windows, or **GPU MTL0: … model layers offloaded** on Mac.
2. Return to the mod settings. Click **Проверить и продолжить** (“Check and continue”) if the instructions are showing; otherwise click **Перевести все моды**. This scans installed mods for missing or suspect translations. **Проверить все диалоги** (“Review all dialogue”) is optional and slower.
3. Keep the settings open until **Офлайн-пакет готов** (“Offline pack ready”) appears. This confirms the game saved the pack. Now load your save. After adding or updating mods, repeat preparation to refresh it.

![Illustration: select Перевести все моды, start the helper if asked, select Проверить и продолжить and wait for Офлайн-пакет готов before loading a save.](assets/prepare-offline.png)

Quitting the game stops the helper and unloads the model from memory. Model files stay on disk for next time. If you quit during preparation, reopen the game, start the helper again and repeat step 3. Completed rows in the helper cache are reused.

### If something doesn't work

- **The mod is missing:** Check the two-file layout above. An extra enclosing folder, an unextracted ZIP or the helper in place of the mod won't work. Restart after activation.
- **The game can't find the helper:** Open the game first, then use the exact launcher for your platform. Wait for the ready message, then click **Проверить и продолжить**. Do not disable SmartScreen or Gatekeeper to run a blocked download.
- **GPU check failed:** Check the GPU driver and available GPU memory; Windows also needs the x64 runtime above. No CPU or cloud fallback is used.
- **A line stays untranslated:** The mod reads supported localization tables, not lettering baked into images or every custom interface. It may skip text it can't translate reliably. For dialogue, try the optional full review.
- **“0 строк для офлайн-перевода” instead of “ready”:** No rows were saved to the new pack. Existing Russian text still works. Check that the mods you expected to translate have finished downloading and contain supported text tables.
