# Autonomous-Driving-via-RL
Applying RL algorithm methods for autonomous driving in Carla simulator.
####  Sensors used - Camera and Lidar

    Requirements
    1) gym
    1) Carla 0.9.6 from https://github.com/carla-simulator/carla/releases/tag/0.9.6
    2) Install gym style wrapper from https://github.com/cjy1992/gym-carla
    3) PyTorch
    
    Training & Testing (for DQN) -
    1) Clone
    git clone https://github.com/akjayant/Autonomous-Driving-via-RL/
    2) Go to CARLA_0.9.6 directory & run the simulator in non-display mode.
    /CARLA_0.9.6$ DISPLAY= ./CarlaUE4.sh -opengl -carla-port=2000
    3) Train from repo root directory
    cd DQN_discrete_drive
    python train.py
    4) Test your agent
    python test.py
  

### 1) DQN Model built on Discrete Actions and primitive reward function : [DQN_Discrete_drive](https://github.com/akjayant/Autonomous-Driving-via-RL/tree/main/DQN_Discrete_drive)
    # ver 1.0
    single path concat - Concat CAMERA and LiDAR frames and extracts features froom it.
    # ver 2.0
    Uses 'state' which contains lateral distance error,speed, presence of vehicle infront etc observation from environment as well.
    multipath - Treats CAMERA and LiDAR frames seperately, extracts features from respective CNN and then concat.
    single path concat - Concat CAMERA and LiDAR frames and extracts features from it.
    
      - Does okay on straight roads & slightly curve roads and follows lane on roundabouts occasionally.
      - Fails on sharp turns.
      - Avoids collisions after training (when speed is slow) but during explorations,it does collide.
      - At faster speeds, collision still occurs.
     # ver 3.0
     Safe exploration during training -
     python safety_train.py False
     python saftey_train.py True
     python train.py
      - Explores safely than previous versions during training. (Applies brakes when out of lane/ obstacle ahead in same lane).
      - at faster speed collsion still occurs. Requires better vision features like semantic segmentation, depth map etc. and longer past frames.
     # ver 4.0 
      Safe Exploration + Better Vision features + More past frames in state represenation - WIP

ver 2.0 -
![p](https://github.com/akjayant/Autonomous-Driving-via-RL/blob/main/DQN_Discrete_drive/ver%202.0/Single%20path%20concat/20201209_001339.gif)

### 2) DDPG Agent built on contionous actions and primitve reward function -[DDPG_Continuous_drive](https://github.com/akjayant/Autonomous-Driving-via-RL/tree/main/DDPG_Continuous_drive) 
    Doesn't work quite well as of now!
 
