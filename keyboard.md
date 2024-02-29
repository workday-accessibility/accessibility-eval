# Keyboard Accessibility testing on mobile devices

# Setup
## Which keyboard should you get?
Any bluetooth keyboard should work. If you are testing both iOS and Android, it is worth having a dedicated keyboard for each. If you are working alone and would like to save money, you can use one keyboard for two devices. It is more convenient if you get a multi-device keyboard because they allow switching between multiple paired devices instead of having to constantly unpair and pair. Another way to use one keyboard with multiple devices is with Apple’s Magic Keyboard which can be connected using bluetooth to an iPhone and using USB-C to a Google Pixel.

## Setting up a bluetooth keyboard on iOS
1. Pair your keyboard with your iPhone by going to `Settings > Bluetooth` and setting Bluetooth `On`.
2. Choose your bluetooth keyboard.
3. Before using your keyboard, enable Full Keyboard access by going to `Accessibility > Keyboards > Full Keyboard Access`.

### Setting up a bluetooth keyboard on Android
1. Pair your keyboard with your Android device by going to `Settings > Connected Devices > Pair new device`. 
2. Upon connection, you get a prompt confirming the keyboard type.

## Discovering the keystrokes
### Android’s keyboard shortcuts
After connecting the keyboard, go to `Settings > System > Languages & Input > Physical Keyboard > Keyboard Shortcuts`.
This will display a list of keyboard shortcuts.

The shortcut list uses a search icon which may be present on some keyboards such as the Logitech K480 and the Logitech K780. On other keyboards, such as Apple’s Magic Keyboard, this corresponds to the command key. 

The list of shortcuts shown does not show how to perform some critical actions like navigating between the top bar and the main content and the keystrokes cannot be re-mapped.Refer to our keystrokes table for a full list.

### iOS Full Keyboard Access Commands
Go to `Settings > Accessibility > Keyboards > Full Keyboard Access > Commands`.

This gives a full list of the commands and allows re-mapping and recording keyboard shortcuts.

## Keystrokes for testing on Android

|                                                                    Action                                                                    |     Magic keyboard    |      Logitech K480       | [keyboard model] |
|----------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|--------------------------|------------------|
| Navigate to the next interactive element                                                                                                     | `Tab`                 | `Tab`                    |                  |
| Navigate to the previous interactive element                                                                                                 | `Shift + Tab`         | `Shift + Tab`            |                  |
| Scroll/Go to next item in group <br /> Select items in a collection, list, or menu                                                           | `Arrow keys`          | `Arrow keys`             |                  |
| Activate an interactive element                                                                                                              | `Enter` or `Spacebar` | `Enter` or `Spacebar`    |                  |
| Go Back. This can be used to dismiss menus and popups.                                                                                       | `Command + Backspace` | `Search-icon key + back` |                  |
| Exit                                                                                                                                         | `Esc`                 | `Esc`                    |                  |
| Switch between apps                                                                                                                          | `Option + Tab`        | `Alt + Tab`              |                  |
| Switch between panes such as top navigation pane and main content [^1]                                                                       | `command + Tab`       | `Search-icon key + Tab`  |                  |
| Open keyboard shortcuts list. <br /> - The shortcuts for Home, Back and Notifications use the search-icon key which is just the command key. | `command + /`         | `Search-icon key + /`    |                  |

[^1]: On Android 14, switching between panes is done with control + tab

## Keystrokes for testing on iOS

|                                       Action                                       |    Magic keyboard   | Logitech K480 | [keyboard model] |
|------------------------------------------------------------------------------------|---------------------|---------------|------------------|
| Navigate to the next interactive element                                           | `Tab`               |               |                  |
| Navigate to the previous interactive element                                       | `Shift+Tab`         |               |                  |
| Scroll/Go to next item in group <br /> Select items in a collection, list, or menu | `Arrow keys`        |               |                  |
| Activate an interactive element                                                    | `Space bar`         |               |                  |
| Show Help                                                                          | `Tab + H`           |               |                  |
| Go Back. This can be used to dismiss menus and popups.                             | `Tab +  B`          |               |                  |
| Exit                                                                               | `Esc`               |               |                  |
| Show Custom Accessibility Actions                                                  | `Tab + Z`           |               |                  |
| Switch between apps                                                                | `Function-Up Arrow` |               |                  |


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
			<li>iOS:
				<ol start="1" type="i">
					<li>if an action is not available, check if there are custom actions. Also try Tab + G to perform keyboard gestures. Depending on interpretation, keyboard gestures may not be a viable alternative for meeting 2.1.1.</li>
				</ol>
			</li>
			<li>Android:
				<ol start="1" type="i">
					<li>if an action is not available. Open the  keyboard shortcuts list to check for any alternative methods to perform an action.</li>
					<li>if you cannot access the top navigation pane or other segment of the screen, check if you can reach the area by using the “switch between panes” keystroke.</li>
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
			<li>When navigation sequences affect meaning and operability, focusable components need to receive focus in an order that preserves meaning and operability.</li>
			<li>The focus order should generally follow the top to bottom start to end reading order but it may divert from this if the order.</li>
			<li>When modals appear focus should be set on them and when dismissed, focus should be returned to the triggering element.</li>
		</ol>
	 </li>
	<li>Ensure keyboard focus is visible.
		<ol start="1" type="a">
			<li>Users should always be able to tell which element has keyboard focus.</li>
			<li>iOS:
			<ol start="1" type="i">
				<li>The default FKA indicator is enough and it can be customized in the Full Keyboard Access settings. </li>
			</ol>
			</li>
			<li>Android:
				<ol start="1" type="i">
					<li>The default focus indicator tends to be very faint. In cases where the developer has not modified the default Android styles (unlikely), then the default indicator is sufficient.</li>
				</ol>
			</li>
		</ol>
		<li>When any user interface component receives focus, ensure it does not initiate a change of context. Note: this is unlikely to occur on native mobile apps.</li>

</ol>

