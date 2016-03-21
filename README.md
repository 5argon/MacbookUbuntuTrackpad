# Macbook Force Touch Trackpad tuning for Ubuntu

## What is it

If you are dual booting the Macbook with Ubuntu, chance are that your god-like touchpad is now getting more and more annoying for various reasons. (This proves that Apple engineer did excellent job on both hardware and software together)

For touchpad lovers like me this is not acceptable. Luckily Ubuntu's Synaptic driver and its corresponding `synclient` allows tuning of various parameters.

Some settings might differ from person to person, even so this might be a good starting point for further tweaking. This settings tried to get the touchpad working in Ubuntu as close to OSX as possible. However there is some flaws that I did not address yet.

This is for Macbook with **Force Touch trackpad**, if you wish to use it with earlier Macbooks, you might want all the `TapButton` to be `1` to enable tapping.

## Improvements from the default Ubuntu settings

- Palm checking turned on.
- Palm checking sensitivity changed so that you can use the side of your thumb to move the mouse while in touch typing position without the driver consider that as a palm, while the thumb in arching position. When resting your thumb fully, it will be considered a palm as I believed this is not a typing hand shape.
- Tap to click all turned off, as Force Touch trackpad uses the force-feedback click.
- Two finger click works as right click, Three finger click works as middle click. (Three finger to paste from highlighted text without hitting copy command)
- Edge scrolling all turned off.
- Two finger scrolling turned on for both axis.
- Scolling is reversed to "natural scroll"
- Scrolling speed and inertia/friction is reduced to be more like in OSX.

## Installation

1. Clone or download the repo so you have the **50-synaptics.conf** file.
2. Make sure `/etc/X11/xorg.conf.d/` directory exist. Put the file or symlinking it to that directory.
3. Restart and see if it works or not. (Or try `synclient` command and see if the values corresponds to that in the `.conf` file.
4. If it is not working, GNOME might be overriding your configuration. Download and use `dconf-editor`

`sudo apt-get install dconf-editor`

Then dig down the tree to `org.gnome.settings-daemon.plugins.mouse` and deactivate the `active` option.

## Missing

- Two finger gesture to forward-backward in web browser. Might require more plugins.
- When palm detection activates, your mouse is disabled until you lifted the touch. In OSX, palm detection runs continuously and seamlessly transition between states without lifting finger.
- Two finger scrolling is not as fine as in OSX. In OSX, scrolling a webpage is a bliss, as the webpage responds **exactly** to your finger as if you are really grabbing the page. In Ubuntu, scrolling moting seemes to translate to discreet number of certain steps. (You will notice this when scrolling slowly.)
- Ubuntu has noticable delay of two finger scrolling. Try two-finger **flicking** the webpage, it is far less satisfying than in OSX.
