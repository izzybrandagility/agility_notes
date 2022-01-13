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
 *
