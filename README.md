# Bolted-connection-in-Salome-Meca-Code_Aster
How to model bolts with heads and contact in SM/CA.

Mechanical engineers know there are many different possibilities to model bolts in FEA. The following how-to shows a possible solution with modeled heads, contact in the underheads and shafts modeled with POU_DE elements (bar elements in CA).

First, make sure to have the bolts modeled in 3D, there is no need to model the threads in bolts or bodies. We do not need them. Move the bolts exactly to their underhead area, where they will be mounted.
Cut off the shafts, only leave the heads for later use. Make sure, the underhead area is a partition of both the head and part. Make a partition of the bolt shafts and the thread bore in the other part (this will be the surface where the lower node of the bar element is connected).
Draw lines, that will substitue the FREE length of the shaft (from upper end of thread area to bottom center of bolt head). These will be modeled with the bar elements later. Name everything you need appropriately (bolt shaft, both nodes in the shafts, underhead areas, all volumes etc.).
Mesh all parts and build a compound mesh.
Import this compound mesh into Asterstudy. See .comm file above for the rest. Once you've mastered this, 20-30 bolts in one model are quite easy. However, it is quite a lot of work, though. With contact, attaching springs SOMEWHERE in the model always makes sense if convergence is problematic.
The important thing about this model is, the pretensio has to be calibrated. The set value for 'N' (SIEG_ELGA_R) will be reduced depending on the stiffness of the parts and bolt heads. Thus, the value in t=1 (relaxed bolts) is the value you want to compare, for example with VDI2230. The main advantage of this model is, once the bolts are settled, you may do everything you want with this model (for example: heat the parts). The evolution of bolt stress can easily be observed by evaluating the tension in the bar elements.
This type of model worked very well for me in the past. Possible further complications are: friction in underhead areas, temperature etc.

Geometry (red lines in bores symbolize the bar elements):
![Bildschirmfoto vom 2023-03-06 17-47-08](https://user-images.githubusercontent.com/89903493/223176032-447b4762-642d-457b-b3a8-c49954ace546.png)

Result in t=2 with force applied (displacement exaggerated):
![Bildschirmfoto vom 2023-03-06 18-01-44](https://user-images.githubusercontent.com/89903493/223179685-85d8af51-ca0e-419d-b5dd-f5ef0c5f2b58.png)
