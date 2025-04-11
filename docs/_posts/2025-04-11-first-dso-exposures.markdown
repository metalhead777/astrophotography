---
layout: post
title:  "First Deep Space Object Exposures"
author: "Niels Fliedner"
date:   2025-04-11 11:50:00 +0100
categories: exposure
---
<script type="text/javascript" async
 src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

My first tests with Deep Space Object (DSO) on analog film were successfull!

# Parameters

- $$TM$$: Measured exposure time
- $$TA$$: Adjusted exposure time, with reciprocity failure correction applied
- $$\text{EV_100}$$: The exposure value with reference to ISO 100. This value is calculated using $$TM$$, so before reciprocity failure correction!

# Setup

For the steps described below, I used the following components:

- A Teleskop with camera-guided tracker inside a dome, including guiding software and focus motor control
- A Bahtinov mask
- Two analog cameras with the same lens mount; one for open-back focussing, one for taking the pictures.
- A lockable shutter-release cable
- A separate focussing screen with a 3D-printed mount
- A (black and white) film with very good [reciprocity](https://en.wikipedia.org/wiki/Reciprocity_(photography)) characteristics
- A stopwatch or timer
- Loads of adapters
- A notebook for writing down the parameters while shooting

## Teleskope

I used the PlaneWave CDK17 Astrograph f/6.8 of the OWL University of Applied Sciences and Arts' [observatory](https://www.th-owl.de/sternwarte/).

The adapters are: `Telescope 2" -> M68 long tube -> Omegon 2" to T2 Nosepiece Adapter -> T2 to Minolta Mount`.

Also, the observatory has a [Bahtinov mask](https://en.wikipedia.org/wiki/Bahtinov_mask), which fits this telescope, for focus finding.

### Tracking

The tracking camera was set to [9 Aurigae](https://theskylive.com/sky/stars/9-aurigae-star).

## Cameras

I used two cameras of the same model, one for finding the focus and one for taking the actual shots.
While this is not strictly necessary, it makes it easier to adjust the telescope focus without having to unload and reload the film in between.
As long as cameras with the same lens mount are used, I don't expect any measurable [flange focal distance](https://en.wikipedia.org/wiki/Flange_focal_distance) differences between them.

### Focussing Camera

I used a Minolta X-700 with its back removed.
Then, I added a Nikon D2X focussing screen with a 3D-printed mounting frame.
This method should resemble open-back focussing mostly done with large-format cameras.

#### Focussing Screen

I used a Nikon D2X focussing screen, which was the cheapest available option at that time.
It features a fresnel lens on the usually smooth side.
Another desired feature was the lack of any focussing aid, such as center prisms.
These would interfer with focus finding, if the reference star is placed close or in the center, since there is no more smooth, matte surface for the Bahtinov interference pattern over the full frame.

The 3D-printed mounting frame was designed to place the the fresnel lens of the focussing screen towards the film rails, and the matt side towards the viewer.
I drew this from [this post by user pluton on nikongear.net](https://nikongear.net/revival/index.php?PHPSESSID=d37e987a8cba6d25b0d900f4c6510500&topic=4970.msg78414#msg78414), which showed a very similar focussing screen inside a Nikon camera.
This might still be wrong though, since it would move the plane of focus on the matte surface further back by the thickness of the focussing screen.
However, when I flipped the focussing screen back to front, the fresnel lens created a lot of distortion when not viewed from the exact center. 

#### Calculate Depth of Focus

I calculated the [depth of focus](https://en.wikipedia.org/wiki/Depth_of_focus) $$db_\pm$$ based on the [circle of confusion](https://en.wikipedia.org/wiki/Circle_of_confusion) $$Z$$:

The circle of confusion maximum diameter can be estimated at $$Z = d/1500$$, with $$d$$ being the diameter of the sensor or film.
For 35 mm film: $$Z = 0.029\,\text{mm}$$ ([Source](https://en.wikipedia.org/wiki/Circle_of_confusion#Circle_of_confusion_diameter_limit_based_on_d/1500)). 

Using the f-number of the telescope $$N = 6.83$$, we can compute the depth of focus:

\\[db_\pm \approx N \cdot Z=6.83 \cdot 0.029\,\text{mm}=\pm 0.198\,\text{mm}\\]

So, all focus errors should remain within $$\pm 0.198\,\text{mm}$$ of the film emulsion layer(s).
Since the focus motor of the PlaneWave CDK17 has a resolution of $$1\,\text{µm}/\text{step}$$, the limiting factor will be the precision of our focussing screen mounting system.
I measured it with calipers, and the distance between the fresnel lense front and the mounting frame surface touching the film guide rails was less than $$\pm 0.1\,\text{mm}$$.

As a side note, the film base thickness should be taken into account, if we would focus from the film pressure plate.
However, this does not apply here, since the focus screen is set to the film guide rails, same as the film's emulsion layer(s).

### Film-holding Camera

I used another Minolta X-700 with a shutter-release cable.

## Film

I used Fujifilm Neopan 100 Acros II, shot at box speed (ISO 100), without any alterations or hypersensitization.

# Steps

## Finding Focus with Bahtinov Mask

1. Move the telescope focus to the home position.
2. Choose one very bright star and keep it in the center of the image frame. I used [Dubhe α Ursae Majoris](https://theskylive.com/sky/stars/dubhe-alpha-ursae-majoris-star).
3. Add the [Bahtinov mask](https://en.wikipedia.org/wiki/Bahtinov_mask) to the teleskope.
4. Find focus using the focussing camera with open back and focussing screen added
	1. Set the camera to "bulb" mode, connect a shutter-release cable with locking function.
	2. Load the camera shutter, then fire and lock the shutter in open position using the shutter-release cable. Keep the shutter open while focussing.
	3. Move the telescope focus slowly and manually, monitor the Bahtinov interference pattern. 
		1. Check the [Wikipedia page](https://en.wikipedia.org/wiki/Bahtinov_mask) on how this pattern is interpreted.
		2. I used a 12x loupe for actually seeing the Bahtinov interference pattern on the focussing screen. It was still difficult, since single stars are not that bright!
5. If you are happy with your focus, write down the stepper settings for repeatability. For me it was `6044` steps from the home position.
6. Remove the Bahtinov mask. Don't forget this step, or your star field photo might look quite unusual.

## Taking Shots

1. Remove the focussing camera, then add the film-holding camera. Do not apply too much force, since it might affect your focus.
2. Set the camera to "bulb" mode, connect a shutter-release cable with locking function.
3. Load the camera shutter, then fire and lock the shutter in open position using the shutter-release cable. At the same time, start your timer.
4. Keep the shutter open until you reached the desired exposure time.
5. Close the shutter by unlocking the shutter-release cable.
6. Reload the shutter and move the frame for the next picture. This usually happens in a single step with analog cameras, but when in doubt, check your specific model.

# The Results

The following images are unaltered with the exception of the watermark.
No further editing or clean-up has been performed.
All images are developed and scanned by [NIMM FILM](https://www.nimmfilm.de/) in Leipzig, Germany.

## Bahtinov Interference Pattern Tests

I took multiple photos with different exposure times to later check the Bahtinov pattern for focus accuracy.
Below are the resulting images in descending order of their exposure time.

<img src="{{ '/assets/img/2025-04-11-first-dso-exposures-02.jpg' | relative_url }}" />

Exposure time ($$TA$$): 00:21:34 h ($$TM$$: 00:15:13 h, $$\text{EV_100}$$: -`4.29`)


<img src="{{ '/assets/img/2025-04-11-first-dso-exposures-01.jpg' | relative_url }}" />

Exposure time ($$TA$$): 00:16:00 h ($$TM$$: 00:11:17 h, $$\text{EV_100}$$: `-3.86`)


<img src="{{ '/assets/img/2025-04-11-first-dso-exposures-03.jpg' | relative_url }}" />

Exposure time ($$TA$$): 00:14:30 h ($$TM$$: 00:10:15 h, $$\text{EV_100}$$: `-3.72`)


<img src="{{ '/assets/img/2025-04-11-first-dso-exposures-05.jpg' | relative_url }}" />

Exposure time ($$TA$$): 00:04:10 h ($$TM$$: 00:02:57 h, $$\text{EV_100}$$: `-1.92`)


<img src="{{ '/assets/img/2025-04-11-first-dso-exposures-04.jpg' | relative_url }}" />

Exposure time ($$TA$$): 00:02:03 h ($$TM$$: 00:01:27 h, $$\text{EV_100}$$: `-0.9`)


## Bahtinov Mask Focus Evaluation

To evaluate if my achieved focus is any good, I drew some lines into the pattern.

<img src="{{ '/assets/img/2025-04-11-first-dso-exposures-02-edit1.jpg' | relative_url }}" />

When looking very closely at the intersection in the middle, a lack of symmetry is clearly visible.
The brown line is drawn through a ray orthogonal to the center red line.
Since the blue line and red line are crossing the same intersection, the red line is clearly off.

Unfortunately, I didn't not the orientation of the Bahtinov mask in relation to the camera.
Without this information, it is not possible to judge whether the focus is too close or too far.

<img src="{{ '/assets/img/2025-04-11-first-dso-exposures-02-edit2.jpg' | relative_url }}" />

So, it becomes appareant, that the focus was not perfect.
This hints either to personal lack of skill, or indeed wrong mounting of the focussing screen.

## Starfield Test

The starfield coordinates at March 4th 2025, 22:47:00 UTC+1
	- Rec. Ascension: 05:02:53.8
	- Declination: 51:11:15.5 desc.

<img src="{{ '/assets/img/2025-04-11-first-dso-exposures-06.jpg' | relative_url }}" />

Exposure time ($$TA$$): 00:45:00 h ($$TM$$: 00:31:56 h, $$\text{EV_100}$$: `-5.36`)

I'm quite pleased with this first "blind" test!
Due to the relatively short exposure time leading to an exposure value of only `-5.36` I expected the resulting image to be much darker.
Or rather, I expected the negatives to be not dense enough.
I ignore this technicality for now, since I didn't receive the negatives back yet, only the scans.

While researching, I found that deeper star fields might require an exposure value closer to `-9`.
For example, computing the measured time $$TM$$ of the first 3 images from Jase Film's excellent video [35mm Astrophotography | Jase.Film | Ep. 2](https://www.youtube.com/watch?v=VlncWFS5xMA), I arrived at an $$\text{EV_100}$$ of `-9.07`.

Of course, there are some obvious flaws.
The streaks in the image are probably caused by either telescope tracking errors or vibrations, or due to wind shaking the telescope.
Maybe I used the focussing screen the wrong way around, which might be a reason for blurry stars.
Also, there is very obvious vignetting, which I assume is caused by the telescope optics. 
When performing astrophotography with modern digital cameras, this would be removed using flat frames.

# How to Improve

There are a few things I could improve here:

- Use Minolta A-mount digital camera for focus finding and then a Minolta A-mount analog camera for the film photos
	- Alternative: use a digital camera with macro lens and a few seconds of exposure to read the interference pattern from the focussing screen
- Check and maybe fix the telescope tracking to avoid streaks.
- Remove vignetting in with reference flat frames, then edit the film photos.
- Check again how the focussing screen should be oriented. Maybe it's better to not have a fresnel lens in there, so I can actually put the matte side towards the lens/telescope.
- Write down the Bahtinov mask orientation in relation to the camera for later focus evaluation.