# Keyboard accessibility testing on mobile devices

# Setup
## Which keyboard should you get?
Any bluetooth keyboard should work. If you are testing both iOS and Android, it is worth having a dedicated keyboard for each. If you are working alone and would like to save money, you can use one keyboard for two devices. It is more convenient if you get a multi-device keyboard because they allow switching between multiple paired devices instead of having to constantly unpair and pair. Another way to use one keyboard with multiple devices is with Apple’s Magic Keyboard which can be connected using bluetooth to an iPhone and using USB-C to a Google Pixel.

## Setting up a bluetooth keyboard on iOS
1. Pair your keyboard with your iPhone by going to `Settings > Bluetooth` and setting Bluetooth `On`.
2. Choose your bluetooth keyboard.
3. Before using your keyboard, enable <abbr title="Full Keyboard Access">FKA</abbr> (Full Keyboard Access) by going to `Accessibility > Keyboards > Full Keyboard Access`.

### Setting up a bluetooth keyboard on Android
1. Pair your keyboard with your Android device by going to `Settings > Connected Devices > Pair new device`. 
2. Upon connection, you get a prompt confirming the keyboard type.

## Discovering the keystrokes
### Android’s keyboard shortcuts
After connecting the keyboard, go to `Settings > System > Languages & Input > Physical Keyboard > Keyboard Shortcuts`.

> [!NOTE]  
> These steps were reproduced on a Pixel 5a running Android 13.

This will display a list of keyboard shortcuts.

<img src="images/image1.png" alt="Android keyboard shortcuts" width="250"/>

The shortcut list uses a search icon which may be present on some keyboards. On the Logitech K480 and K780 models, the search icon corresponds to the start key. On Apple’s Magic Keyboard, this corresponds to the command key. You may need to experiment and confirm to determine what this is on your keyboard.

The list of shortcuts shown does not show how to perform some critical actions like navigating between the top bar and the main content but this is provided in the full keystroke table below (action: Switch between panes). Also, Android keystrokes cannot be re-mapped.


### iOS Full Keyboard Access Commands
Go to `Settings > Accessibility > Keyboards > Full Keyboard Access > Commands`.

This gives a full list of the commands and allows re-mapping and recording keyboard shortcuts.

<img src="images/image2.png" alt="Apple keyboard shortcuts mapping" width="250"/>


## Keystrokes for testing on Android

|                                                                    Action                                                                    |     Magic keyboard     |      Logitech K480       | Logitech K780                    |
|----------------------------------------------------------------------------------------------------------------------------------------------|------------------------|--------------------------|----------------------------------|
| Navigate to the next interactive element                                                                                                     | `tab`                  | `tab`                    | `tab`                            |
| Navigate to the previous interactive element                                                                                                 | `shift + tab`          | `shift + tab`            | `shift + tab`                    |
| Scroll/Go to next item in group <br /> Select items in a collection, list, or menu                                                           | `arrow keys`           | `arrow keys`             | `arrow keys`                     |
| Activate an interactive element                                                                                                              | `enter` or `space bar` | `enter` or `space bar`   | `enter` or `space bar`           |
| Go Back. This can be used to dismiss menus and popups.                                                                                       | `command + backspace`  | `search-icon key + back` | `start + left arrow` or `back/F6`|
| Exit                                                                                                                                         | `esc`                  | `esc`                    | `back/F6` or `home/F4`           |
| Switch between apps                                                                                                                          | `option + tab`         | Android 13 or lower: `alt + tab` <br/>Android 14 and up: `alt + tab` or `start + tab` | Android 13 or lower: `alt + tab` <br/>Android 14 and up: `alt + tab` or `start + tab`|
| Switch between panes (navigation clusters) such as top navigation pane and main content                                                                        | Android 13 or lower: `command + tab`<br/>Android 14 and up: `control + tab`| Android 13 or lower: `start + tab` <br/>Android 14 and up: `control + tab` | Android 13 or lower: `start + tab` <br/>Android 14 and up: `control + tab` |
| Open keyboard shortcuts list. <br /> - The shortcuts for Home, Back and Notifications use the search-icon key which is just the command key. | `command + /`         | `start + /`             |`start + /` <br/>(Does not work with numpad  `/` key)   |


## Keystrokes for testing on iOS

|                                       Action                                       |    Magic keyboard   | Logitech K480    | Logitech K780 |
|------------------------------------------------------------------------------------|---------------------|------------------|------------------|
| Navigate to the next interactive element                                           | `tab`               |    `tab`         |  `tab`           |
| Navigate to the previous interactive element                                       | `shift + tab`       |  `shift + tab`    | `shift + tab`     |
| Scroll/Go to next item in group <br /> Select items in a collection, list, or menu | `arrow keys`        |  `arrow keys`    |  `arrow keys`    |
| Activate an interactive element                                                    | `space bar`         |  `space bar`     |  `space bar`     |
| Show Help                                                                          | `tab + h`           |  `tab + h`       |   `tab + h`      |
| Go Back. This can be used to dismiss menus and popups.                             | `tab +  b`          |   `tab +  b`     |  `tab +  b`      |
| Exit                                                                               | `esc`               |   `esc`          |  `back/F6` or `home/F4`  |
| Show Custom Accessibility Actions                                                  | `tab + z`           |  `tab + z`       |   `tab + z`          |
| Switch between apps                                                                | `function + up arrow` | Double-press `back/F4` |  Double-press `back/F6`    |


# Testing
## Overview of keyboard testing procedure
|                                             Test Steps                                             |                                WCAG SC                                 |
|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| Ensure all actions can be performed by keyboard.                                                   | [2.1.1 Keyboard](https://www.w3.org/WAI/WCAG21/Understanding/keyboard) |
| Ensure there are no keyboard traps                                                                 | [2.1.2 No Keyboard Trap](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap) |
| Ensure the focus order is logical.                                                                 | [2.4.3 Focus Order](https://www.w3.org/WAI/WCAG21/Understanding/focus-order) |
| Ensure keyboard focus is visible                                                                   | [2.4.7 Focus Visible](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible) |
| When any user interface component receives focus, ensure it does not initiate a change of context. | [3.2.1 On Focus](https://www.w3.org/WAI/WCAG21/Understanding/on-focus) |
| Ensure character key shortcuts without modifiers can be remapped or turned off                     | [2.1.4 Character Key Shortcuts](https://www.w3.org/WAI/WCAG21/Understanding/character-key-shortcuts) |
| Ensure content which appears on focus, is persistent and dismissable.                              | [1.4.13 Content on Hover or Focus](https://www.w3.org/WAI/WCAG21/Understanding/content-on-hover-or-focus) |
|                                                                                                    |                                                                        |

## Full keyboard testing procedure

<ol start="1" type="1">
	<li>Ensure all actions can be performed by keyboard.
		<ol start="1" type="a">
			<li><strong>iOS:</strong>
				<ol start="1" type="i">
					<li>If an action is not available, check if there are custom actions. Also try <code>tab + g</code> to perform keyboard gestures. Depending on interpretation, keyboard gestures may not be a viable alternative for meeting 2.1.1.</li>
				</ol>
			</li>
			<li><strong>Android:</strong>
				<ol start="1" type="i">
					<li>If an action is not available. Open the  keyboard shortcuts list to check for any alternative methods to perform an action.</li>
					<li>If you cannot access the top navigation pane or other segment of the screen, check if you can reach the area by using the “switch between panes” keystroke.</li>
				</ol>
			</li>
		</ol>
	</li>
	<li>Ensure there are no keyboard traps.
		<ol start="1" type="i">
			<li>If an element receives keyboard focus, it should be possible to move focus away using standard inputs or there are instructions to guide users.</li>
		</ol>
	</li>
	<li>Ensure the focus order is logical.
		<ol start="1" type="a">
			<li>When navigation sequences affect meaning and operability, focusable elements need to receive focus in an order that preserves meaning and operability.</li>
			<li>The focus order should generally follow the reading order: top to bottom and start to end. However, the focus order can also differ as long as the order makes sense for the activity. </li>
			<li>When a popup appears focus should be set on the new content and when dismissed, focus should be returned to the triggering element.</li>
		</ol>
	 </li>
	<li>Ensure keyboard focus is visible.
		<ol start="1" type="a">
			<li>Users should always be able to tell which element has keyboard focus.</li>
			<li><strong>iOS:</strong>
			<ol start="1" type="i">
				<li>The default <abbr title="Full Keyboard Access">FKA</abbr> indicator is enough and it can be customized in the Full Keyboard Access settings. </li>
			</ol>
			</li>
			<li><strong>Android:</strong>
				<ol start="1" type="i">
					<li>The default focus indicator tends to be very faint. In cases where the developer has not modified the default Android styles (including background color and button color), then the default indicator is sufficient. But in the much more unlikely case of custom focus styles, the developer must ensure the focus indicator is sufficient and should adjust the default to ensure the contrast ratio is at least 3:1.</li>
				</ol>
			</li>
		</ol>
	</li>
	<li>When any user interface component receives focus, ensure it does not initiate a change of context. <strong>Note:</strong> this is unlikely to occur on native mobile apps.
		<ol start="1" type="a">
			<li>Ensure elements receiving focus do not cause any of the following:
				<ol start="1" type="i">
					<li>Forms submitted automatically;</li>
					<li>New windows are launched;</li>
					<li>Focus jumps to another component;</li>
					<li>A different app or user agent is activated;</li>
					<li>Content is changed that affects the meaning of the screen/page;</li>
				</ol>
			</li>
		</ol>
	</li>
	<li>Ensure character key shortcuts without modifiers can be remapped or turned off.
		<ol start="1" type="a">
			<li>Try inputting all of the alphabet, punctuation, number and symbol characters. If any of these keys are used alone then make sure one of the following is true:
				<ol start="1" type="i">
					<li>There is a mechanism available to turn the shortcut off;</li>
					<li>A mechanism is available to remap the shortcut to include one or more non-printable keyboard keys (e.g., <code>ctrl, alt/option</code>)</li>
					<li>The keyboard shortcut for a user interface element is only active when that element has focus.</li>
				</ol>
			</li>
		</ol>
	</li>
	<li>Ensure content which appears in focus, is persistent and dismissable. <strong>Note:</strong> this is unlikely to occur on native mobile apps.
		<ol start="1" type="a">
			<li>Where receiving keyboard focus triggers additional content to become visible and then hidden, the following are true:
				<ol start="1" type="i">
					<li>Dismissible: A mechanism is available to dismiss the additional content without moving keyboard focus, unless the additional content communicates an input error or does not obscure or replace other content;</li>
					<li>Persistent: The additional content remains visible until the focus trigger is removed, the user dismisses it, or its information is no longer valid.</li>
					<li>(Hoverable is not applicable to mobile because it is only for mouse hover.)</li>
				</ol>
			</li>
		</ol>
	</li>
</ol>


# References
## Apple iPhone
* [	Adjust the onscreen and external keyboard settings on iPhone - Apple Support](https://support.apple.com/guide/iphone/adjust-keyboard-settings-ipha7c3927eb/ios)
* [Use shortcuts on Magic Keyboard with iPhone](https://support.apple.com/guide/iphone/use-shortcuts-iph3da414515/17.0/ios/17.0)
* [Pair Magic Keyboard with iPhone](https://support.apple.com/guide/iphone/pair-magic-keyboard-iph4288319c0/17.0/ios/17.0)

## Google Android
* [Use TalkBack keyboard shortcuts](https://support.google.com/accessibility/android/answer/6110948?hl=en#zippy=%2Cdefault-keymap)
* [Use accessibility shortcuts](https://support.google.com/accessibility/android/answer/7650693?hl=en)
