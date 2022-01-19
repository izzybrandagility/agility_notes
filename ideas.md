#### Learn a coordinate transform (offline) that improves the QP for WBC.

Someone mentioned that the QP WBC doesn't perform well near the extremes, because the true dynamics are being approximated. Maybe we can learn a warping of the state space such that solving the QP in this new space results in better performance near these extremes.

#### More generally: learn a residual for any reduced order model

We use simplified models to enable real-time MPC. Maybe we can learn the residual of the simplified model when compared to a more complete model offline, and then use that residual online.

#### 
