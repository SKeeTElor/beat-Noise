---
title: Phase Problem Correction
date: September 30th, 2025
---

# Abstract

In this report, I will simply discuss the phase probelm wihthin the data processing procedure, to be specific, I want to do mutiple short time measureent and use fourier transfomation to get the power spectrum in frequency domain. I will fist discuss how shoud we "take average" of those repeated measurement, then I gonna point out there is a phase problem that gonna cause our signal decrease, and we will discuss the possible solution to this problem.

# Background

Consider our free-lunch experiment: We gonna do negative feedback for t1, then quickly do positive feedback for t2, then we measure the signal (added by modulated signal) for t3, for our cantilever, the t3 is approximatly 0.3s. For a epoch, assume the sampling rate is S, then for the forourier transformation , the upper bond gonna be S and the resolution would be 3 Hz. We conclude that the short measuremen time t3 gonna bring us 2 problems, the first one gonna be the resolution of our power spectrum, the 2nd problem is we naturally want more data(longer measurement time). This motivete us repeating this procedure, then we gonna have N epochs of this short time measurmnet data. We assume between each procedure, there is a time delay t4. If we simply take the average of all of those signal, we won't have a higher resolution (if we do discrete ft) in the frequency domain. This problem can be ignored for now, we disscuss it in other notebooks(it is not a really problem). However, if we want to do N measurment, I gonna run into the problem that each measuremnt will have a phase incoherent delta phi.

To our experiment, if we care about the freq shift, our signal gonna looks like a series of square wave, as we are turning on and off the pos feedback/rf wave. We can eliminate the phase problem by forcing the start of measurement to be exactly the same point with the start of signal process, by this way we make the signal for each measurment to be exactly the same, so we eliminate our phase prblem.

To the amplitude signal, we are tracking the movemnt of our cantilever, if we trust our positive feedback, we gonna assume the our cantilever always starts at the apex, that makes our signals would be phase coherent.

However, there is also another phase problem in the pos feedback, this refers to we are not driving the cantilever at the right phase, which make our postive feedback less efficiency. But for the freq shift, this is probably not the reason why our signal decrease.

In conclusion, to solve the phase problem for freq shift: add a clock to our signal generator, make the control sequence being indentical for each run; for amplitude signal, make a good positive feedback.

PS: there is another way discussed in Degen's paper for signal that we can't control its phase evolvement.