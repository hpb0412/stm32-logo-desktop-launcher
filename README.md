# STM32 Cube Desktop Launcher

> **Disclaimer**: All assets and names belong to [ST](https://www.st.com/). I just collect the appropriate assets to ensure the tools function in the right way on my machine.

When I install the STM32 Cube toolset, none of them have a proper logo display on the task bar of Ubuntu (a.k.a favorites bar). So I decide to *hack* it.

## STM32CubeMX

Create a file named `cubemx.desktop` at `/usr/share/applications`.
(Select whatever name you like as long as it doesn't exist there).

```conf
[Desktop Entry]
Version=6.0.1
Type=Application
Name=STM32CubeMX
GenericName=CubeMx
Comment=STM32CubeMX
Exec=/your_path_to/STM32CubeMX/STM32CubeMX
Icon=/your_path_to/stm32cude-desktop-launcher/stm32cubemx.png
Terminal=false
Categories=Development;IDE;Electronics;
Keywords=embedded electronics;electronics;stm;microcontroller;
```

## STM32CubeIDE

Since this tool is installed automatically through an `sh` script,
we don't need to manually create the `.desktop` file inside `/usr/share/applications`.

File the file `/usr/share/applications/st-stm32cubeide-{version}.desktop`, and edit the `Icon=` line.
Example `st-stm32cubeide-1.4.0.desktop`:

```conf
Icon=/your_path_to/stm32cude-desktop-launcher/stm32cubeide.png
```

Next, do the same thing (update logo path) for this file `~/.local/share/applications/stm32cubeide.desktop`

**Done!**

## Explanation

For STM32CubeMX, it's quite straight forward. We have a single execution file, so we simply provide a single `.desktop` with proper logo file (a `.png`).

For STM32CudeIDE, we have 2 execution files. This is because this IDE is built on top of Eclipse IDE. Technically, they are calling the launcher first, and the launcher, in turn, calls the real IDE. That is the reason why we need to modify 2 files to make the job done.

## TODO

I am quite lazy after discover this workaround. Maybe next time, I will add an `sh` script to make the job automatically.

I am not sure if the `disclaimer` above is suitable or not. If you think you can help. Please suggest. Thanks!
