**Use SQ`T2prep to hold diffusion gradients, and performed before TFE and TSE readout**


**Gradients**
--

* Set diffusion gradient slope to 0.9ms.  Under enhanced mode, it's advised to make slew rate<100mT/m/s. GR strength<45mT/m; Under max mode, GR slew rate<200mT/m/s, GR strength<22.5mT/m
* Adding some space after RF.
* Fixed DP eddy current compensation Gradient dur to 7ms.
* Using existing gradients for stimulated echo forming while keeping the CPMG condition. (This is wiser than put the single refocusing gradient after RF. That strategy was implemented in the other branch already). Dephasing gradient still at the end of t2prep, but it copies the Gradient in DP-TSE. For TSE acquisition, the strength is determined by a control parameter. 
* Adding recalibration for non-m1 nulling twice refocusing diffusion gradients 


**RF pulase**
--

* Use composited tip-up RF pulse.
* Use composited refocusing RF pulse.

*BIR4 refocusing RF pulses implementation*



**Other issues**
--

* Turn off phase encoding gradient to measure FID signal to get better understanding of the sequence physics
* Reset the lower limit for TSE startup echo in TSE with 3D view to 0 with DP function enabled.
* Add global saturation RF pulse. To make Mz the same before each shot no matter how heartbeat changes
