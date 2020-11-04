# Table Of Contents

- [Introduction](#introduction)
- [Installing Software](#installing-software)
- [Configuring Software](#configuring-software)
- [Configuring Flight Simulators](#configuring-flight-simulators)
- [Recommended Settings](#recommended-settings)
- [Troubleshooting](#troubleshooting)

# Introduction

AITrack and Opentrack are both free, open source tools you can use to start using head-tracking in your flight simulators. All you need is a webcam or a smart phone connected to your PC. In this tutorial, I'll try to simplify the setup process and provide some recommended settings for improving your overall experience with AITrack and Opentrack experience.

You'll need both AITrack and Opentrack to get started, and here' why:
1. AITrack takes your webcam feed and intelligently tracks your face (using AI), mapping it to what I'll call "movement data"
2. Opentrack takes this "movement data" and converts it to a useful protocol that your flight sims understand

Most of these steps are covered on (and some text even copied verbatim from) the [AITrack User Guide](https://github.com/AIRLegend/aitrack/wiki/User-guide), but I've included some additional screenshots and explanations along the way.

# Installing Software

### Visual C++ Redistributable x64

Download and install [Visual C++ Redistributable x64](https://aka.ms/vs/16/release/vc_redist.x64.exe) in case you don't already have it.

![Visual C++ Redistributable x64](/images/visual-c-install.jpg)

Only one button to click here to install.

### AITrack

AITrack does not come with an installation file. Download the most recent version of the tracker from the [releases page](https://github.com/AIRLegend/aitracker/releases) (`.zip` file) and extract its content. NOTE: Do not download the source code.

![AITrack](/images/aitrack-link.jpg)

### Opentrack

Download Opentrack from [Opentrack's releases page](https://github.com/opentrack/opentrack/releases). Be sure to choose the file that ends with `.exe`, like this:

![Opentrack](/images/opentrack-link.jpg)

Open this `exe` file, click next a few times, and you're set.

# Configuring Software

The key to obtaining good results with this program lies on tweaking all the parameters (both on AITrack and Opentrack).

### AITrack

After you've extracted the zip file you downloaded, you should find an `AITrack.exe` file. After opening, you should see something like this:

![AITrack UI](/images/aitrack-ui.jpg)

Click the Configuration button.
1. The most important parameter AITrack has is the "**Distance**" parameter, which is the distance, in meters, at which your webcam is in straight line from your face. If you have problems with your recognized position, try fine-tuning it. However, it doesn't need to be ultra precise (no need to get a ruler ;)). 
2. Model type should be set to "Fast"
3. Set "FPS" to 60. The higher the number, the smoother the response. If you computer has difficulty running at 60, you can change this back to 30.
4. Click "Apply" and close the Configuration window.
5. That's it. Now click "Start", and AITrack will begin tracking your face.

Now for this to be useful, you'll need to configure Opentrack. See the next section.

### Opentrack

Opentrack will take all the "movement data" and send it to your flight simulator.  Open Opentrack and use the following steps to configure:

1. For "Input" dropdown on this first screen, change this to "UDP over network"
2. Click the hammer icon next to "UDP over network". Port should be "4242", and the values for yaw, pitch, and roll should be "0"."
3. For "Output" dropdown on this first screen, this should be set to "freetrack 2.0 enhanced"
4. The "Filter" should be set to "Accela". Click the hammer and use the following settings:
    - Smoothing (Rotation filtering) = 1.55 degree
    - Deadzone (Rotation filtering) = 0.03 degree
    - Smoothing (Position filtering) = 0.8 mm
    - Deadzone (Position filtering) = 0.85 mm
5. When I tested AITrack, two of the axis were backwards. To fix this, I clicked the "Options" button, and on the "Output" tab I checked the "Invert" checkbox for both Pitch and Z. I also changed "Roll" to "Disabled", but this is completely personal preference.

Your settings should now look something like this:

![Opentrack](/images/opentrack-configs.jpg)
![Opentrack](/images/opentrack-output.png)

The last thing we're going to take a look at are the Opentrack "curves". They represent the mapping between how much you move your head in the real life and how much the view is moved in game. You can configure them by clicking "Mapping" in Opentrack.

These mappings are **very user specific**. I sit 6 feet in front of a 65" television, but you might be using a completely different configuration. I will provide a screenshot of all my mappings, but please realize **it's very possible you'll need to tweak these to get them just right for you and your setup**.

Take a look at this video: [Tweaking your curves in Opentrack](https://www.youtube.com/watch?v=u0TBI7SoGkc), which explains the process pretty well. As a final recommendation, try to add a deadzone near 0 on every axis in order to have a comfortable neutral head position.

Again, I recommend changing the curves to something you're happy with, but here are mine (NOTE: I have changed the "Max input" dropdown on some):

![Opentrack](/images/opentrack-yaw.png)
![Opentrack](/images/opentrack-pitch.png)
![Opentrack](/images/opentrack-roll.png)
![Opentrack](/images/opentrack-x.png)
![Opentrack](/images/opentrack-y.png)
![Opentrack](/images/opentrack-z.png)

Ok, after everything is configured, you should be able to click the Start button and see the pink octupus moving around (NOTE: AITrack must also be running in the background at the same time).

Check out the recommended settings below for a few more tips.

# Configuring Flight Simulators

### XPlane 11

1. Open X-Plane 11
2. Click the "Settings" button the on main screen.
3. Under the "Graphics" tab, click the checkbox at the bottom labeled "Enable TrackIR and TrackHat view tracking in 3-D cockpit"

![XPlane](/images/xplane-settings.png)

You should now be able to move your head in XPlane. See the [recommended settings](#recommended-settings) below for some useful tips.

### Microsoft Flight Simulator

No settings need to be enabled; headtracking is enabled by default in Microsoft Flight Simulator.

See the [recommended settings](#recommended-settings) below for some useful tips.

# Recommended Settings

Here are just a couple more settings I strongly recommend to make your experience that much better when using head tracking.

### Center Button

Sometimes you'll want to reset the "Center" position of your head. 

1. Open "Options" in Opentrack.
2. On the shortcuts tab, click the "Bind" button next to "Center".
3. Press a button on your flight controller or a keyboard combination.
4. Click "OK" to save.

Now anytime you're flying and want to re-center your head, look at and aim your head directly at the center of your display and press this center button.

### Pause Headtracking Button

Sometimes you'll want to lock your head position, or essentially pause the movement of headtracking. 

1. Open "Options" in Opentrack.
2. On the shortcuts tab, click the "Bind" button next to "Toggle".
3. Press a button on your flight controller or a keyboard combination.
4. Click "OK" to save.

Now anytime you're flying and want to lock the camera in it's current position, press this button. To resume headtracking, just press the button again.

# Troubleshooting

This space left open to add any tips and suggestions.
