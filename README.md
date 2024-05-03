# zephyr-vscode-example

This is an example configuration for setting up Visual Studio Code for Zephyr application development. It was originally created for the talk entitled, "[Zephyr & Visual Studio Code: How to Develop Zephyr Apps with a Modern, Visual IDE](https://youtu.be/IKNHPmG-Qxo)" at EOSS 2023.

## Infineon AIROC™ CYW20829 Bluetooth® LE MCU Evaluation Kit (CYW920829M2EVK-02)

The original example has been modified to demonstrate Zephyr application development targeting the Infineon CYW920829M2EVK-02 Evaluation Kit.

Early Zephyr support for CYW920829M2EVK-02 is currently available in pull request #70961, ["boards: arm: Introduce Infineon CYW920829M2EVK-02 board"](https://github.com/zephyrproject-rtos/zephyr/pull/70961).

## Example details

There are many, many different ways to develop a Zephyr application. This example currently assumes:

* In-tree development
* Building `samples/basic/thread` so we can demonstrate thread-aware debugging
* Targetting CYW920829M2EVK-02

## Steps

1. Follow the Zephyr [Getting Started Guide](https://docs.zephyrproject.org/latest/develop/getting_started/index.html) for your OS
1. Check out pull request with CYW920829M2EVK-02 support
    - `git fetch origin pull/70961/head`
    - `git checkout FETCH_HEAD`
1. Turn on Compilation Database with `west config build.cmake-args -- -DCMAKE_EXPORT_COMPILE_COMMANDS=ON`
1. Copy the `zephyr.code-workspace` file and/or the `.vscode` folder to `samples/basic/thread`
1. See board [doc](https://github.com/sreeramIfx/zephyr/blob/1e2c711baa45347ba2100acd4ecee13d357560b4/boards/infineon/cyw920829m2evk_02/doc/index.rst) for the CYW920829M2EVK-02
    - Install `srec_cat`
    - Install ModusToolbox
1. Open `samples/basic/thread` in VS Code
    - Accept to install recommended extensions
1. Edit settings in `.vscode/settings.json` and/or `zephyr.code-workspace` to reflect the actual paths used
    - `modustoolbox.toolsPath`
    - `zephyr.zephyr_base`
1. Set the `Python: Interpreter Path` in VS Code settings
    - If Python virtual environments were used during install, this would be something like:
	    - `~/zephyrproject/.venv/bin/python3`
1. Add led1 alias in board file `zephyr\boards\infineon\cyw920829m2evk_02\cyw920829m2evk_02-common.dtsi`
    ```
    aliases {
		led0 = &user_led0;
		sw0 = &user_bt0;
		led1 = &user_led1;
		sw1 = &user_bt1;
	};
    ```
1. Try the different build tasks and the flash task
1. Try to connect over the serial terminal
1. Try step debugging

## Credits

https://zmk.dev/docs/development/ide-integration
