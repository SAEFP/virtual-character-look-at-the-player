## How can you make a Metahuman look at the VR player?👁️‍🗨️ ##
   
In the current project, participants and the virtual character engage in social interactions. Eye contact is a significant aspect of social interactions. This repository will explain how to make a metahuman maintain eye contact with the player.
   
Example video of the Metahuman looking towards the VR player:

<img src="./images/Looking-At-The-Player-gif.gif" alt="Looking-At-The-Player-gif" width="500"/> 
   
## 📝Steps for creating a VR Character looking at the VR Player`s head: ##
  
1.	Create a new BP class under the Content folder in UE and name the character “BP_AI_ToLook”.
   
2.	Open the BP. Select the Mesh (CharacterMesh0) under the Components section. 
   
3.	For the Skeletal Mesh Asset under the Mesh in Details section, Select “SKM_Manny_Simple”. 
   
4.	Adjust the rotation of the mesh to -89 on the Y axis and -90 on the Z axis. 
   
5.	To create the animation blueprint, right click on the content folder. Select “Animation”> “Animation Blueprint”. Then Select “SK_Mannequin” under the Specific Skeleton and click on Create.
   
6.	Name the Animation BP  “ABP_AI_ToLook”.
   
7.	Open the Animation BP and then open the AnimGraph.
   
8.	Place the “MM_Idle” animation into the Anim Graph and connect it with the Output Pose. 
   
9.	Enable “Loop Animation” under the Details section.
    
10.	Go the BP_AIToLook. 
   
11.	Assign the animation blueprint (ABP_AI_ToLook) you created to the character`s blueprint (BP_AI_ToLook) by selecting “ABP_AIToLook” for the Anim Class under the Details section.
   
12.	Open the Event Graph in the “ABP_AIToLook”.
   
13.	Create a “Cast To VRPawn” node and use “Get Player Pawn” as an object. 
   
14.	Right click on the Event Graph and create “Get Socket Location”.
    
15.	Click on the Return Value and select “Promote to variable”. Name this variable “Look At Pos”. 
   
16.	Go to the AnimGraph and add a “Look At” node. 
   
17.	Select Look At node and choose the head for the “Bone to Modify” under the Details section. 
   
18.	Select “Expose to Pin” for Look at Location under the Target in the Details section.  
   
19.	Drag and drop “Look At Pos” from Variables to the Look At Location on the Look At node.
   
20.	Adjust the Look At node settings to ensure natural movement. Set Clamp Angle as 55 degrees (maximum angle) and set the Interpolation Time to 3 for smooth transitions under the Look Up Axis tab in Details section.
   
21.	Your virtual character should now look at the VR player`s head. 👁️‍🗨️
   
**Blueprints of the Looking At The Player**
   
**Event Graph 🏃**   
   
<img src="./images/ABP_EventGraph.png" alt="ABP_EventGraph" width="800"/> 

**Animation Graph 🏃** 
   
<img src="./images/ABP_AnimGraph.png" alt="ABP_AnimGraph" width="800"/> 
   
## 📝Steps for integrating Metahuman body to the Metahuman BP: ##

1.	Open both BP_AI_ToLook and your Metahuman blueprint.
   
2.	In the Viewport tab of your Metahuman, select the Body under the Components section.
   
3.	Click the folder icon in the Skeletal Mesh Asset under the Details section.
   
4.	Go to the BP_AI_ToLook character. Select Mesh (CharacterMesh0).
   
5.	Click on the arrow icon in the Skeletal Mesh Asset under the Details to replace it with the MetaHuman character's body.
   
6.	Go to the MetaHuman BP, copy all MetaHuman components (body, legs, torso, face) by selecting them, and then go to the BP_AI_ToLook character and paste them into the BP_AI_ToLook character’s Mesh (CharacterMesh0).
   
7.	If the MetaHuman parts are not positioned correctly, select them, and use the reset arrow to align them properly.
8.	Go back to the MetaHuman BP, select all face components, copy, and paste them onto the BP_AI_ToLook character, under the face component.
   
9.	Copy and paste the LODSync component as well.
   
10.	Select the Mesh (CharacterMesh0), click the folder icon in the Skeletal Mesh Asset under the Details. Select the body of the MetaHuman. Right-click, select Skeleton, and then select Assign Skeleton.
   
11.	Choose the SK_Mannequin skeleton and accept.
   
12.	Repeat the skeleton assignment for each MetaHuman component (torso, legs, feet) to ensure they use the SK_Mannequin skeleton.
   
13.	Open the BP_AI_ToLook character, set the Animation Class under the Details section to the ABP_Quinn_C.
   
14.	To adjust alignment issues, go to the Construction Script, dragging in torso, legs, and feet components, and using "Set Relative Post Component" to correct their positions relative to the main mesh.
   
15.	Compile and save the animation blueprint.
   
**Blueprint of the integrating Metahuman body to the Metahuman BP**
   
<img src="./images/BP_AI_ToLook_ConstructionScript.png" alt="BP_AI_ToLook_ConstructionScript" width="800"/>    
   
References   
Here is the video I used for creating a VR Character looking at the VR Player`s head:https://www.youtube.com/watch?v=8skq8t_Fffk&list=PLqQpJGVeCiLH58DAlPWRCUrVvPkeZRC2e&index=15   
   
Here is the video I used for integrating Metahuman body to the Metahuman BP: https://www.youtube.com/watch?v=fz2-N-6hQNU&list=PLqQpJGVeCiLH58DAlPWRCUrVvPkeZRC2e&index=7
