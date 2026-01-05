---
title: Hardware V2.0
tags:
- tag1
- tag2
---

## **Alterations Looking Forward**

While for some the schematic can appear confusing, we can use that as a starting point for things that might be done differently. As one of the major issues during testing was ensuring that the Op-amp worked as it was designed. This was because the teaching team for 304 works better with a pictographic representation of the Op-amp. Unfortunately, this would have also increased complexity in the pcb and therefore, increased the likely hood of footprints not matching real parts. However, in the schematic having the pictographic format would help communicate an idea as opposed to the balance of a part. As for PCB design one element I'd definitely work on would be where I was placing the screw terminals. As when I was building it I realized I made a grave error when predicting how the footprints would interact with the parts. Specifically I made it so the screw terminals were facing into other parts because my brain got trapped in their free roaming position in the schematic. Thankfully I had screwed up a little bit on the footprint of another piece and was able to get everything to fit but it was not an ideal solution. Therefore, double checking the footprints as well as placing anything that needs later attachments at easy to reach positions would be key parts of my next version for this project.

### **Utilizing Footprints From Manufacturer**

One thing that I noticed with this project is that the EGR 304 teaching team wanted us to create our own footprints for parts. However, places like Digikey contain the footprint and the datasheet for a part. This means that I could have ensured my footprint was correct either through an additional validation step or through utilization of the developers footprint. This would have helped with the FAN8100N footprint due to the difference between pins and the fan piece. With that said it was a good learning tool in Cadence and forced me to figure out some more parts of the software.
