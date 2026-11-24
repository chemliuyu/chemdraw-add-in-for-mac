English | [简体中文](README_CN.md)

<div align="center">

![ChemDraw Add-in for Mac — Draw, paste, and edit again.](assets/banner.svg)

# ChemDraw Add-in for Mac

[Download 2.0.1](https://github.com/BoeingART/chemdraw-add-in-for-mac/releases/tag/2.0.1) · [Installation guide](docs/installation.md) · [Changelog](CHANGELOG.md)

</div>

**Editable ChemDraw structures in Microsoft Word, PowerPoint and Excel for Mac.**

Copy a chemical structure in ChemDraw, paste an editable drawing into Office, and double-click it to keep editing. Open existing Windows ChemDraw OLE objects in Mac ChemDraw and save changes back to the original Office document while keeping the editor open. Each drawing retains its editable source and preview.

## Version 2.0.1

**2.0.1 is the first stable release in the 2.0 series**, published on 11 November 2026. Its source is maintained on [`dev-2.0`](https://github.com/BoeingART/chemdraw-add-in-for-mac/tree/dev-2.0); the [`2.0.1` tag](https://github.com/BoeingART/chemdraw-add-in-for-mac/tree/2.0.1) records the released code.

- **Native ChemDraw OLE:** paste CDX structures into Word, PowerPoint and Excel as native OLE objects, and edit existing embedded ChemDraw structures. CDXML and older drawings use the vector-carrier compatibility path.
- **Save and continue editing:** Command-S and menu Save synchronize the saved structure and preview to the original Office document. New, unsaved documents are supported; synchronization preserves subsequent input and tracks the original target when switching documents or using Save As.
- **PowerPoint:** edit structures inside groups while retaining companion pictures, cropping, captions and stacking order. Identical copies pasted into a presentation can now be opened and edited independently; saving updates the selected copy.
- **Word:** update the drawing in its original range, with hidden save staging to prevent temporary window flashes, duplicate drawings and layout shifts. Save and recovery checks include Track Changes.
- **In-app updates:** fix the processor architecture check that interrupted installation, allowing the application to be replaced and reopened automatically.

Word and PowerPoint have application-level paste, open and save validation records. Excel's native OLE implementation has file-format and transaction checks; application testing with Excel installed remains pending. See the [Word and Excel results](docs/word-excel-native-ole-results.md), [Word save results](docs/word-ole-in-place-results.md) and [PowerPoint OLE results](docs/ole-save-performance-results.md).

## Demo

![ChemDraw Add-in for Mac demo](assets/demo.gif)

## Install and configure

Requires **macOS 12 or later**, **ChemDraw** and **Office for Mac**, installed and activated separately. Word, PowerPoint and Excel are supported.

1. Download the universal DMG from the [2.0.1 release](https://github.com/BoeingART/chemdraw-add-in-for-mac/releases/tag/2.0.1), open it, and drag the app into **Applications**. It supports Apple Silicon and Intel Macs. When replacing an older version, finish the current structure edit and quit the add-in first.
2. Open the installed app. First-run **Add-in Setup** checks file access for Word, PowerPoint and Excel, Accessibility, and paste-helper readiness. Only installed Office hosts are required.
3. Allow the requested access. Setup registers the add-ins, verifies writing and read-back, and starts the helper automatically. Click **Done** when ready.
4. For later updates, choose **Check for Updates** from the menu bar. After confirmation, the app downloads its update, replaces itself and reopens automatically. Existing permissions, certificates and drafts are retained. An active structure edit finishes before the update continues. If an older version reports an architecture error during installation, install the 2.0.1 DMG manually.
5. If an Office access grant is missing, open setup or choose **Repair Add-in**. Adding Excel may require its first file-access and Automation grants.

Closing the window keeps the helper running in the menu bar. Reopen the app from Applications to restore a hidden icon. The menu shows the current version. Updates show download progress and can be cancelled; after installation, the app reopens automatically.

## Paste and edit

1. Open a new or existing Word document, PowerPoint presentation or Excel workbook.
2. Select a structure in ChemDraw and copy it with **⌘C**.
3. Paste in Office with **⌘V**, right-click **Paste**, or the panel's **Paste editable drawing / 粘贴可编辑绘图** button.
4. Double-click the drawing to edit it in ChemDraw. Press **⌘S** or choose **Save** to update the original Office image and continue editing. Close the ChemDraw document to return to the original Office document.
5. Save your Office document whenever you choose. New, unsaved documents support direct paste, opening, and write-back.

Pasting during an existing edit creates an independent drawing. The original edit keeps its Office document and ChemDraw target through window switches and Save As. The panel and setup window show operation progress, specific failure reasons, and the next action.

## Local data and recovery

Certificates, captured structures, and editing drafts remain in `~/Library/Application Support/ChemOffice/work` across upgrades. Each Office app exchanges previews through its own sandbox cache.

Closing the original Word, PowerPoint or Excel document retains the latest local draft and closes its matching ChemDraw editing window. An interrupted edit can be resumed by double-clicking the original drawing. Closed drafts are retained under `recovery` when starting another edit.

The helper captures chemical clipboard data during explicit paste operations, and editing runs locally. The optional Office panel connects to a local HTTPS service; its Office.js library loads from Microsoft's CDN.

## Build and validation

Source builds require Apple's command-line tools with Swift 5.7 or later. Run `zsh scripts/build.sh` for the current architecture or `zsh scripts/build.sh --universal` for Apple Silicon and Intel. See the [installation guide](docs/installation.md) for packaging and signing setup.

PowerPoint OLE command-line tools are available after building:

```sh
build/chemoffice ole-extract input.pptx output.cdx
build/chemoffice ole-export input.pptx edited.cdx new-copy.pptx
build/chemoffice ole-new source.cdx new-presentation.pptx
```

These extract the first ChemDraw object, export an edited presentation copy, or create a new OLE presentation. Choose new output filenames. Run `zsh scripts/test-ole.sh` for OLE transport checks across Word, PowerPoint and Excel and PowerPoint adapter compilation.

Completed checks are recorded in [installation readiness](docs/installation-readiness-results.md) and [unsaved Office document checks](docs/unsaved-office-results.md). Practice documents are in [examples](examples/README.md).

Copyright 2026 ChemDraw Add-in for Mac contributors. Released under the [Apache License, Version 2.0](LICENSE).
