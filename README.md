This is a project related to [Talon](https://talonvoice.com/). It is a set of utility actions and a command generation wizard UI aimed at making it much easier to build new mouse based voice commands for applications.

# Overview of features

There are several features provided by this package:

1. A set of actions in `mouse_helper.py` that make it easier to build mouse based commands in Talon. For example there are actions to save and restore the mouse position, to move the mouse cursor relative to the active window, or to find a saved image on the screen.
2. A UI for indicating positions on the screen in `marker_ui.py` and voice commands to move the cursor to them or click them.
3. A voice command wizard in `command_wizard.py` which lets you more easily build voice commands based on the above features using a GUI.

# Usage

[![Demonstration video](docs/video-demo-thumb.png)](https://talon-ui-helper.s3.ap-southeast-2.amazonaws.com/talon-ui-helper-demo.webm)

1. The GUI: Say "command wizard show". The button text in the menu is also mapped as a voice command (e.g. "choose 1").
2. Select a menu option, select the region.
3. Confirm by pressing enter key, a command is added to your clipboard, paste directly in to a .talon file. After that you only need to choose the actual voice command you want to use to trigger it.

## Available builders

* Single image selection. This builder will allow you to choose a region of the screen to save as an image. This image will be clicked by your voice command.
* Multi image selection. This builder draws a label on each of the matches it finds allowing you to move to the image in question using the 'jump <label>' (e.g. 'jump bat') voice command. 'touch <label>' and 'righty <label>' are also available.
* Find items in a box/blob detector. This allows you to draw a rectangle which will then be searched for clickable regions. The first column of pixels is treated as background, and the rest is foreground. If the box is wider than high, then the first row are the background pixels. Note that the rectangle is relative to the currently window, if window gets moved or resized the voice command should still be able to find the relevant region.

## Settings

The image selector command builder needs a place to save the image templates it generates. By default this is the `image_templates` directory in your Talon user folder. If you'd like to change where these are stored you can use the `user.mouse_helper_template_directory` setting.
