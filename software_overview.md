## Thread Diagram
In order to understand how everything fits together, I'm going to make a diagram showing which threads are running on the robot and the simulator, and how they talk to eachother.

### Questions and things I noticed
 * there appears to be a redundant connection? line `209` and line `307` both connect `perception::setWorldMessageCallback` to `web::getWorldMessage`
 * One "getter" is named `setAction` on line `303`. Is this on purpose?
 * why is `mujoco_sim` not another thread?

## Control

 * Thread callbacks modify `Input` and `Output` structs defined in lines `110-132` of `control/src/control/Thread.cpp`
 * 