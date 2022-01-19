# Notes

### Helpful commands

 * To launch the simulator, from the `control` directory run: `bazel run //src:main simulator.dynamic=false`. The last argument controls _kinematic_ vs _dynamic_ mode.
 * To launch the web interface (including documentation and simulator) go to the `control` directory and run `./ar-control`


### TODO

 * Understand the interaction between bazel, package-control, and docker
 *


### Thoughts from Perception planning meeting 1.11.22

 * rapid data collection idea: AR tag on boxes -- inpaint over the tags to generate synthetic data (based on the pixels at the boundary of the tag)
 * domain randomized pretraining in simulation will greatly reduce the training data requirements for the panoptic segmentation
 * We should consider 3DP3 for pose refinement

### Thoughts from RL Control meeting 1.12.22

 * Most promising solution is to learn a model which takes as input a trajectory to track and the current state, and outputs a residual command which improves the QP controller.
 * I'm not convinced that there are significant gains to be had in control
 * There's a risk that any time the planner changes, and the learned controller is now operating on a different distribution. The implication of this is that _learning will be sensitive to changes in other parts of the stack._

### Prep and thoughts for Planning meeting 1.13.22

 * Questions
    * is it worth it to spend much time on develop, or should I seek to understand the refactored planner
    * Seeking one well scoped short term objective, and one more ambitious objective
    * planning vs control: where are the benefits to be had
    * how much task-level planning is required? box sequencing for unloading trucks?

 * Possible projects
    * 2d path planning improvements (motion primitives, foot placements)
    * contact proposal distribution (more researchy)
    * 

### Notes from internship project planning meeting

 * talk to pedro and patrick regarding configuration of the truck unloading simulation
 * work with taylor on the truck unloading simulator (75%)
 * work with dan B on the state estimator (25%)

### Notes from reading about EKFs

 * The problem with EKFs is that they linearize around the estimate mean to compute the kalman gain. If the estimate is way off, the resulting kalman gain may not result in convergence [mentioned here](https://arxiv.org/pdf/1410.1465.pdf).
 * 