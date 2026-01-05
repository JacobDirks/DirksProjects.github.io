---
title: Power Budget
tags:
- tag1
- tag2
---

## **Overview**

After selecting components in [*Component Selection*](https://jacobdirks.github.io/02-Component-Selection/Component-Selection/) we needed to ensure that the subsection would have the power it needs with the added requirement of a safety margin. Therefore, we took the active components, meaning we excluded switches and passive components, and ensured our power supply as well as our regulators were able to get the power needed. The specifications for each piece came from their datasheet except in the case of the motor where it will only get power through the motor driver so it has different tolerances.

![budget1](DirksDocs/powerBudget1.PNG){style="max-height:400px;"}

![budget2](DirksDocs/powerBudget2.PNG){style="max-height:400px;"}

## **Conclusions**

A single barrel jack port that is delivering 9V and 3A into the system is sufficient for the needs of the subsystem. If needed we have some power left over that we could add some new features after getting client feedback. However, we do not need the full 3A capabilities and could get away with around .8A going through a fuse into the system.

## **Resources**

The power budget is available in other forms such as a [*pdf version*](DirksDocs/powerBudget.pdf), and as a [*Microsoft Excel Sheet*](DirksDocs/PowerBudgetEGR304T102.xlsx).
