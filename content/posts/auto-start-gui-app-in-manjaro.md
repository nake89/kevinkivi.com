---
title: "How to autostart any GUI app in Manjaro"
date: 2021-04-30T20:33:00+02:00
draft: false
---

In this example I will autostart the GUI package manager of Manjaro.

Create a file e.g. `~/.config/autostart/pamac-manager.desktop`
In that file put
```
[Desktop Entry]
Terminal=false
Name=pamac-manager
Type=Application
Exec=/usr/bin/pamac-manager
Icon=pamac-manager
Comment=Package Manager
```

In the `Exec` line put the path to your executable file. The rest you can probably guess.

Source: https://specifications.freedesktop.org/autostart-spec/autostart-spec-latest.html
