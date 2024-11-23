---
title: Calciol Production
date: 2024-11-15
draft: false
tags:
  - Calciol
  - Cholecalciferol
  - Production
  - Skin
  - D3
  - UVB
  - Calculator
---

# Cholecalciferol Production
<div class="abstract">
When exposed to sunlight, your skin produces vitamin D. How much you create depends on your skin type, time in the sun, and how much skin is exposed. We can estimate this using two simple steps. First, we calculate how much vitamin D your skin makes per square centimeter per minute based on UV radiation and daylight hours. Then, we adjust that number for how long you’re outside, how much skin is exposed (like arms, legs, and face), and your skin type. For example, exposing 5,000 $cm^{2}$ of skin to the sun for 30 minutes will produce more vitamin D if done around noon when UV rays are strongest. Always avoid sunburn!
<div class="centered">
For more technical details, read on.
</div>
</div>

When our skin is exposed to UVB rays, e.g., during sun exposure, [Cholecalciferol](calciol) aka [Calciol](calciol)  is produced from 7-Dehydrocholesterol. In a 1977 publication, PC Beadle estimated that about 160 IU [Cholecalciferol](calciol) could be produced at 40° Latitude when exposing 1 $cm^{2}$ of skin to the sun for the whole day. Dark skin would produce around 70 IU under the same conditions. This information is suboptimal to drive the decision of how to expose oneself to the sun.

We would like to estimate the amount of [Cholecalciferol](calciol) we produce during exposure to the sun for a short period of time (say 30 minutes) and for a certain amount of exposure, say 5,000 $cm^{2}$, which would be legs, arms, and face. We might want to adjust the estimate to our skin type as well. Most importantly, we should have a good estimate of the UVB radiation. For all of this, let’s develop two formulas.

$$IU_{[Cholecalciferol](calciol)​}/min \times cm^{2} = 2,500 × E_{daily} ​/ t_{daylight} \tag{1}$$

$E_{daily}$​: The daily portion of UV radiation relevant for D3 in kJ/$m^{2}$.  
$t_{daylight}$: Total Daylight Time in minutes.  

We can find yesterday’s or other past UV doses at [TEMIS](https://www.temis.nl/uvradiation/uvdose.php) (a number between 0 and 14). This number should be plugged in for Edaily. Then we need the minutes of daylight which we can find for example at [timeanddate](https://www.timeanddate.com/sun/). Calculate the minutes and plug it in for tdaylight. That provides us with the IUs of [Cholecalciferol](calciol) that one $cm^{2}$ skin can produce in one minute at the given settings time of year and location.

Next we would be interested in using this rate, adjusting it to the area exposed and the skin type. for this we will use the following formula.

$$ IU_{Total} = t_{exposed} \times I_{Uper} \, \text{J}/cm^{2} \times K_{skin} \times A_{exposed} \tag{2}$$

$I_{Uper}$ J/$cm^{2}$​: [Cholecalciferol](calciol) (Vitamin D₃) production per joule per cm²  
$K_{skin}$: Skin type factor.  
$t_{exposed​}$​: time of exposure to the sun in minutes.  
$A_{exposed}$: Area of skin exposed (cm²).  
$IU_{Total}$: Total vitamin D₃ produced in IU.


What we can calculate here are rough estimates since UVB radiation is different throughout the day and strongest around noon. So sunbathing at 7 a.m. will probably do you no good in terms of [Cholecalciferol](calciol) production, but at lunchtime, depending on the season and locale, you will get a good amount of IUs. Check out the converter between IUs and mcgs.

! When exposing yourself to the sun, make sure you never get a sunburn !

You can use the calculator below to estimate how much IU you can produce with the sun exposure you get. This does not consider the physiological limits of the production of [Cholecalciferol](calciol) (a topic for another time).



{{< Dcalc_script >}}






