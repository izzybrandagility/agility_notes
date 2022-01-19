# Notes as I read through IMU EKF

```cpp
void update(const StateEstimate& se,
              const math::Vector3d& rot_vel,
              const math::Vector3d& lin_acc,
              time::AutoTimestamp t);

void getEstimate(FloatingBaseEstimatorStates& se);

void reset(const StateEstimate& se, time::AutoTimestamp t);

void applyBaseCorrection(const math::Vector3d& dx);
```

### update

 * modifies `se` inplace
 * takes in rotation velocity and linear acceleration directly from the VectorNav IMU
 * `197-204` updates the `contact_` map with which EEs are in contact (force threshold)
 * `206-226` predict position and velocity using IMU `lin_acc` (one step of forward euler)
 * `232` if an EE is not in contact, estimate it's position by using the base position and FK
 * `235-274` build Phi, Q, and G (transition, process noise and rotation? respectively)
 * `275-283` predict P_, the state covariance (no measurements yet)
 * `291-311` build Y, H, and N (N is called R on wikipedia)
 * `314-326` measurement update

### getEstimate

loads the most recent state estimate into the supplied pointer, `se`

###

as the name says

### applyBaseCorrection

### unZipStates

Takes in a vector `x` and expands it into new vectors

 * `v` is a 3-vector for the base velocity
 * `c` is a 3-vector for the base position
 * `p` is a map from FrameType to 3-vector contact poses
 * `ba` is a 3-vector, likely accelerometer bias

### vectorNavToFrame

 * return the transform from the VectorNav IMU to the frame (usually an EE frame)