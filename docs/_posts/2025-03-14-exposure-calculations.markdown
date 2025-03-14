---
layout: post
title:  "Exposure Conversions"
date:   2025-03-14 16:19:23 +0100
categories: exposure maths
---

Here are some formulae regarding exposure.

# Parameters

- $$AV$$: Aperture value
- $$\text{EV}$$: Exposure value
- $$\text{EV_100}$$: Exposure value with regard to ISO 100
- $$N$$: F-number (aperture)
- $$T$$: shutter speed

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

# Further Sources

- [Paul Schlyter: "Radiometry and photometry in astronomy - 13. Photography and photometry"](https://www.stjarnhimlen.se/comp/radfaq.html#13)