# Asset Library for Unreal Engine

Keep your reusable assets in one shared library on your machine and move them between projects in one click, with the whole dependency tree.
Editor-only plugin for **Unreal Engine 5.1 - 5.8** (Windows, Win64). Distributed through Fab.

Full reference (PDF): [AssetLibrary_Documentation.pdf](AssetLibrary_Documentation.pdf)

## What it does

- **Save with all dependencies.** Right-click an asset (or drag it from the Content Browser) and it is copied to your library together with everything it references.
- **One-click import into any project.** Open another project, click **Library** in the Content Browser toolbar, pick the asset, import it.
- **Dependency picker.** Choose which dependencies come along, grouped by class.
- **Engine-version awareness.** Every asset is stamped with the engine version that saved it; you are warned before importing from a newer engine.

## New in 2.7.4

- **Folders first.** The library opens at **Library** showing sub-folders first, then the assets directly inside. Double-click a folder to open it; breadcrumbs and the tree take you back. The last folder you used is remembered. Assets can still live in the root.
- **Move folders.** Drag a folder onto another folder (cards or tree) to move it with everything inside. Drop it on Library to send it back to the top. Right-click > **Move to**, **F2** to rename, **Del** to delete.
- **Organise by dropping.** Drop assets onto a folder card to move them, or drop folders/assets from the Content Browser straight onto a library folder.
- **List view** (like Windows Explorer) and **sorting** by name, date and more. Asset names are always shown in full, never cut with "...".
- **Search** looks through the current folder and everything below it. Optional: *Sort > Show > Assets from sub-folders*.
- **Better thumbnails.** Uses the Content Browser renderer, then its own renderers (HDR cube maps, skyboxes), then the thumbnail stored in the asset. If nothing is available you get a clean placeholder and the inspector explains why. Right-click > **Reload thumbnail** rebuilds one on demand.
- **Themes.** Gear menu > Appearance: light and dark themes, accent colours, and the thumbnail background (soft / by asset type / original).
- **Stability.** Fixed a crash when adding assets that depend on Deformer Graph (Optimus) content.

## Install

1. Close the Unreal Editor.
2. Download the zip for your engine version and extract it so you have `Plugins/AssetLibrary/` inside your project.
3. Open the project. A **Library** button appears in the Content Browser toolbar (also under Window > Asset Library).

Builds for 5.1, 5.3, 5.4, 5.5, 5.6, 5.7 and 5.8 are pre-compiled. A build that contains only `Source/` (no `Binaries/`) must be compiled once inside a C++ project.

## Where is the library stored?

Default: `UserDir/UEAssetLibrary` (for example `C:/Users/You/Documents/UEAssetLibrary`). Change it in **Project Settings > Asset Library**. Point it to a synced folder to share it across machines.

## Known limitations

- If an asset references content from a plugin that is not enabled in the destination project, the import will have broken references. Enable the same plugins in both projects.
- Assets saved by a newer engine cannot be loaded by an older one (you get a warning before import).
- Not a multi-user version control system: with a shared library, the last writer wins.
- Engine content (`/Engine/...`) is never copied.

## Reporting bugs

Open an issue and include: engine version (Help > About), plugin version (`AssetLibrary.uplugin`), exact steps, and the relevant lines of the editor log filtered by `LogAssetLibrary`.
