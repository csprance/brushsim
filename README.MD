These scripts will allow you to simulate the physics on a brush object. This is needed because normally you can not simulate a brush. You can only simulate a RigidBodyEx, so my script automates this lengthy process for you.
What it does:
# 1. Gets the selected object.
# 2. Create rigidbodyex and copy model of seleted object to rigidbodyex 'Model' Property
# 3. set rigidbodyex xfroms to match xform of selected object
# 5. hide selected object
# 6. simulate rigidbody ex

You Must then Run the Next Script Which does this:
# 7. after simulation is done copy original objects xfroms to new xforms of simulated rigid body
# 8. delete rigid body.

Why this is useful:
It allows you to expedite item placement and makes complex objects with strange pivots easy to place in the world naturally. Once these scripts are bound to hotkeys you can simply select an object Press One key and then immediately press another key to get a perfectly placed brush in the world.

Run Them from the Python Scripts Panel
View->Open View Pane->Python Scripts
Select Simulatebrush.py to simulate the brush
Select setobj.py to set the transforms and delete the rigidbody

Run The Script Manually
The Script can be run manually from the python Script Terminal 
View->Open View Pane-> Script Terminal

In the terminal copy and paste

general.run_file("simulatebrush.py")
Set Up Hotkeys For Super Speed!
Tools->Configure Toolbox Macros
Create a New Macro by Clicking the  and giving it a name simobject
Copy The Below settings for Simulating the Object Make sure to click Assign!

general.run_file("simulatebrush.py")
Create Another macro by clicking the  and giving it a different name setobj
Copy the Below Settings for Setting the Objects Xforms and deleting the temporary RigidBodyEx named 'brush_sim_temp'

general.run_file("setobj.py")
Create Another macro and give it the name simobjweight
Copy the below settings This will allow you to Set the objects mass instead of just accepting the default mass of 45

general.run_file_parameters("simulatebrush.py", 'weight')
Hit Ok.
Now in the editor you can rapidly select a brush quickly simulate the physics and set the transforms all in just two key presses (I bound mine to Numpad 0 and Numpad 1 and Numpad 3 for setting the weight of the Physicalized object)

Tips On Use and Important Note!
You must ALWAYS run setobj.py after running simulatebrush.py so if you set up the above hotkeys you must always press 0 and then 1 every time.

It's also not a good idea to undo after you run the script. If you don't like the simulation still set the object by pressing 1 and then try again by replacing the object and running the simulation again.

The reason you shouldn't undo is because the script just automates a long process so it keeps that process in undo history.

If something goes wrong first unhide all your objects (Because I hide the original objects to simulate physics)
then look for brush_sim_temp entity and delete it.

You should then be good to go!.



