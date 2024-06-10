# zephyr-vscode-example

This is an example configuration for setting up Visual Studio Code for Zephyr application development. It was originally created for the talk entitled, "[Zephyr & Visual Studio Code: How to Develop Zephyr Apps with a Modern, Visual IDE](https://youtu.be/IKNHPmG-Qxo)" at EOSS 2023.

## Infineon AIROC™ CYW20829 Bluetooth® LE MCU Evaluation Kit (CYW920829M2EVK-02)

The original example has been modified to demonstrate Zephyr application development targeting the Infineon CYW920829M2EVK-02 Evaluation Kit.

## Example details

There are many, many different ways to develop a Zephyr application. This example currently assumes:

* In-tree development
* Building `samples/basic/thread` so we can demonstrate thread-aware debugging
* Targetting CYW920829M2EVK-02

## Steps

1. Follow the Zephyr [Getting Started Guide](https://docs.zephyrproject.org/latest/develop/getting_started/index.html) for your OS
1. Turn on Compilation Database with `west config build.cmake-args -- -DCMAKE_EXPORT_COMPILE_COMMANDS=ON`
1. Copy the `.vscode` folder and/or the `zephyr.code-workspace` file to `samples/basic/thread`
1. See board [doc](https://docs.zephyrproject.org/latest/boards/infineon/cyw920829m2evk_02/doc/index.html) for the CYW920829M2EVK-02
    - Install Infineon customized OpenOCD according to instructions
1. Open `samples/basic/thread` in VS Code
    - Accept to install recommended extensions
1. Edit settings in `.vscode/settings.json` and/or `zephyr.code-workspace` to reflect the actual paths used
    - `zephyr.zephyr_base`
    - `zephyr.zephyr_sdk_install_dir`
    - `infineon.openocd_base`
1. Set the `Python: Interpreter Path` in VS Code settings
    - If Python virtual environments were used during install, this would be something like:
	    - `~/zephyrproject/.venv/bin/python3`
1. Try the different build tasks and the flash task
1. Try to connect over the serial terminal
1. Try step debugging
    - Enable thread awareness support by adding `CONFIG_DEBUG_THREAD_INFO=y` in application file `prj.conf`

## Credits

https://zmk.dev/docs/development/ide-integration
