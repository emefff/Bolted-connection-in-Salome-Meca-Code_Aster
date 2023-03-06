# Bolted-connection-in-Salome-Meca-Code_Aster
How to model bolts with heads and contact in SM/CA

Mechanical engineers know there are many different possibilities to model bolts in FEA. The following how-to shows a possible solution with modeled heads, contact in the underheads and shafts modeled with POU_DE elements (bar elements in CA).

First, make sure to have the bolts modeled in 3D, there is no need to model the threads in bolts or bodies. We do not need them. Move the bolts exactly to their underhead area, where they will be mounted.
Cut off the shafts, only leave the heads for later use. Make sure, the underhead area is a partition of the head and part. Make a partition of the bolt shafts and the thread bore in the other part.
Draw lines, that will substitue the FREE length of the shaft. These will be modeled with the bar elements later. Name everything you need appropriately (bolt shaft, both nodes in hte shafts, underhead areas, all volumes etc.).
Mesh all parts and build a compound mesh.
Import this compound mesh into Asterstudy. See .comm file above for the rest. Once you've mastered this, 20-30 bolts in one model are quite easy. However, it is qwuite a lot of work, though. With contact, attaching springs SOMEWHERE in the model always makes sense.
