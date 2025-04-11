---
layout: post
title:  "Exposure Conversions"
author: "Niels Fliedner"
date:   2025-04-09 22:20:00 +0100
categories: exposure maths
---
<script type="text/javascript" async
 src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

**Updated 09.04.2025. Previous version was created at 14.03.2025**

Here are some formulae regarding exposure.

# Parameters

- $$AV$$: Aperture value
- $$\text{EV}$$: Exposure value
- $$\text{EV_100}$$: Exposure value with regard to ISO 100
- $$N$$: F-number (aperture)
- $$T$$: shutter speed (or more precisely: shutter time)
- $$TM$$: shutter time as measured (for example using a light meter)
- $$TA$$: shutter time, adjusted for reciprocity failure

# Exposure Value

Exposure value $$EV$$, given in reference to ISO 100:

\\[\text{EV\_100} = \log_2 \left( \frac{100\cdot N^2}{\text{ISO} \cdot T} \right)\\]

# Shutter Speed

Solved for shutter speed $$T$$:

\\[T = \frac{100\cdot N^2}{\text{ISO} \cdot 2^\text{EV\_100}}\\]

# F-Number (Aperture)

Solved for aperture $$N$$:

\\[N=\sqrt{\frac{2^\text{EV\_100} \cdot \text{ISO} \cdot T}{100}}\\]

# F-Number and Aperture Value Conversions

The f-number is determined by the lens opening.
It can also be derived from the Aperture Value *AV*:

\\[N=\sqrt{2^{AV}}\\]

For example, with an aperture value $$AV=6$$ we receive the f-number $$N=\sqrt{2^{6}}=8$$

Conversely, we can use aperture values (*AV*) for calculating exposure changes in stops:

\\[AV = \log_2 N^2=2 \cdot \log_2 N\\]

For example, with an f-number of $$N=4$$ we receive the aperture value $$AV=2 \cdot \log_2 4=4$$

## Example: Push 2 Stops

For calculating a push of 2 stops, we first convert the f-number to an aperture value, add $$2$$ for 2 stops, and then convert back to f-number

Let's assume an f-number $$N=16$$.
Converting to aperture value, we receive $$AV=8$$.

When pushing two stops, the aperture value changes as follows: $$ AV_\text{push}=AV-2\,\text{stops} = 8-2=6$$

Converting back to f-number: $$N_\text{push}=\sqrt{2^{AV_\text{push}}}=\sqrt{2^{6}}=8$$

Checking with the [f-number scale](https://en.wikipedia.org/wiki/F-number#Standard_full-stop_f-number_scale), we indeed would go two steps from f/16 to f/8: $$16\rightarrow 11\rightarrow 8$$

Similarly, pulling 2 stops would look like this: $$N_\text{pull}=\sqrt{2^{AV_\text{pull}}}=\sqrt{2^{AV+2\,\text{stops}}}$$

We can summarize the formulae for pushing or pulling $$n$$ stops:

\\[N_\text{push,n}=\sqrt{2^{AV_\text{push,n}}}=\sqrt{2^{AV-n\,\text{stops}}}\\]
\\[N_\text{pull,n}=\sqrt{2^{AV_\text{pull,n}}}=\sqrt{2^{AV+n\,\text{stops}}}\\]

# Reverse-Engineering Measured Time

It can help to look at other analog photographer's work to understand which settings might work for our own experiments.
However, they usually only state what the final (adjusted) exposure time was, but not the originally measured time before reciprocity failure correction.

Luckily, we can reverse-engineer the measured time, as long as we know the film, it's reciprocity correction formula, and the ISO it was shot at.

## Example 01: Film Shot at Box Speed

In this first example we imagine an image shot with Ilford Delta 100 at box speed:

- ISO: $$100$$
- F-number: $$N = 3.5$$
- Exposure time (adjusted): $$TA = 00:45:00\,\text{h}$$ (this is the adjusted time, since it is used for actually taking the photo)

Looking at the datasheet for Ilford 100, we find the formula for the adjusted time:

\\[TA = TM^{1.26}\\]

So, to get to the originally measure time, we inverse the formula:

\\[TM = TA^\frac{1}{1.26}\\]

## Example 02: Reciprocity Correction with Stops

Some films don't have an exponential formula for reciprocity failure correction.
Instead, the datasheet states to correct by a certain amount of stops.
For example, Fujifilm Neopan 100 AcrosII requires an exposure correction of $$1/2$$ stop for exposure times $$120 - 1000\,\text{s}$$.

Reverse-engineering this takes a few extra steps, but is still possible. 
We will use a trick and reversing the exposure-time-based reciprocity failure correction by correcting the aperture with the same amount of stops.
Then, we compute the exposure value.
Afterwards, we find the exposure time that would be necessary to reach the same exposure value with the original f-number.

Let's look at an example:

- ISO: $$100$$
- F-number: $$N = 4$$
- Exposure time (adjusted): $$TA = 00:15:00\,\text{h} = 900\,\text{s}$$
- Stops for reciprocity failure correction: $$n = 1/2$$

1. Convert to aperture value: $$AV=2 \cdot \log_2 N=2 \cdot \log_2 4=4$$
2. Add $$n = 1/2$$ stop: $$AV_\text{adj} = AV + n = 4 + 1/2 = 4.5$$
3. Convert back to f-number: $$N_\text{adj} = \sqrt{2^{AV_\text{adj}}} = 4.76$$
4. Compute the exposure value, using the adjusted f-number and the adjusted exposure time: $$\text{EV_100} = \log_2 \left( \frac{100\cdot N_\text{adj}^2}{\text{ISO} \cdot TA} \right) = \log_2 \left( \frac{100\cdot 4.76^2}{100 \cdot 900\,\text{s}} \right) = -5.31$$
5. Compute the measured time using the original f-number and the exposure value: $$TM = \frac{100 \cdot N^2}{\text{ISO} \cdot 2^{EV\_100}} = \frac{100 \cdot 4^2}{100 \cdot 2^{-5.31}} = 634,73\,\text{s} \approx 00:10:53\,\text{h}$$

As a control, we can take the measured time compute the exposure value. 
If our previous calculations are correct, we should receive the same exposure value as before:

\\[\text{EV\_100} = \log_2 \left( \frac{100\cdot N^2}{\text{ISO} \cdot TM} \right) = \log_2 \left( \frac{100\cdot 4^2}{\text{100} \cdot 634,73\,\text{s}} \right) = -5.31\\]

For calculating everything in one step (if you insist), we could also use the following formula, combining all previous steps into one:

\\[TM = \frac{100\cdot N^2}{\text{ISO}\cdot 2^{EV\_100}} = \frac{100\cdot N^2}{\text{ISO}\cdot2^{\log_2\left(\frac{100 \cdot 2^\left({2\cdot\log_2(N)+n}\right)}{\text{ISO}\cdot TA}\right)}}\\]

## Example 03: Film was additionally pushed one stop

Let's assume the film's exposure should be corrected by $$1/2$$ stop for reciprocity failure correction.
Also, let's assume the film originally was pushed one stop, and the photographer only gave us the adjusted time $$TA$$.
Now, we want to find the originally measured time $$TM$$.

We would proceed exactly the same as in example 02.
But, instead of only applying $$1/2$$ stop for reciprocity failure correction, we also incorporate the push of 1 stop: $$n = 1/2 + 1 = 1.5$$

If the film was pulled instead, we would subtract the stops: $$n = 1/2 - 1 = -0.5$$

# Further Sources

- [Paul Schlyter: "Radiometry and photometry in astronomy - 13. Photography and photometry"](https://www.stjarnhimlen.se/comp/radfaq.html#13)
