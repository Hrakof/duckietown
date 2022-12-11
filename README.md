# Self-driving in Duckietown environment

### Team name: Úristen very deep

|Team members | Neptun|
| :---------- | :---- |
| Debreczeni László | IWNUTK |
| Karmacsi Péter | L94HDE |
| Almási Zsombor | DZR1RM |
  
### Project: Self-driving in Duckietown environment

Gym-Duckietown is a car simulator environment, based on OpenAI Gym environments. The goal of our project is to teach an AI to lane following self-drive in the Duckietown. We are using reinforcement learning to control our Duckiebot.

## Milestone 1
### Files
 - steps_milestone_1.txt : Documentation for the steps of the first Milestone. **This file contains the link to the video of the running environment.**  
 - /gym-duckietown-daffy/custom_maps/my_map.yaml : Custom map for testing the agent of basic_control.py

## Milestone 2
 - Link to a trained model: https://drive.google.com/file/d/1mlSoV7zlqxo3Sd2Uw_nb0NOSbr9vLkjD/view?usp=sharing

### Training, option #1: with the gym
We tried some training with the gym, you just have to `cd` into the `deprecatedtown/training` folder and then run
`python reinforcement/train.py --model-dir=reinforcement/pytorch/models --max_timesteps=10000` you can play with the
`max_timesteps` number freely.
This uses the `DDPG` algorithm for the reinforcement learning.
As you have seen in the video, it is truly not perfect, but our goal was just to make the training work because
the duckietown-gym repo contains a lot of buggy and not runnable code.

### Training, option #2: Stable Baselines3
As an option for training, we have created the train_hw.ipynb file. Training is easier in an interactive notebook, because we can run cells individually. In this implementation we used the Stable Baselines3 library. For a reinforcement learning algorithm, we chose PPO with MlpPolicy.

After the imports, a path for logging and model saving is defined. The environment is created with the helper function of Duckietown. This can be run without any parameters, or a map name to define the map for the environment. We had to create a new Image Wrapper, because the sequence of the data in the wrapper was wrong. Then, we had to create a model with the chosen algorithm and environment, then start the learning process. In the ```learn``` function we can define the number of training steps. At the end, the model is saved automatically to the defined ```model_path```. To check the results, we could use the ```evaluate_policy``` function of Stable Baselines3. We can simply change the map in in the ```launch_env``` helper function to evaluate in a different environment.

We can also load already trained models with the ```PPO.load``` function, which needs the path to the model, and the environment passed as arguments. 

## Milestone 3
We could not achieve great results training with DDPG. The trained models drive almost entirely straight when trained for a short time and start to spin in one place and never move when trained for longer. Setting the time spent taking random actions before learning longer did not improve the situation.

The best performing model mostly spins in one place but in some situations it moves a bit along the road. The model can be found in the [ddpg_best](https://github.com/Hrakof/duckietown/tree/milestone_3/ddpg_best) folder. A video is available [here](https://drive.google.com/file/d/1leOpowgnSdQ6jkxr18vh6QKribBWjlGY/view?fbclid=IwAR10cEzXAnouTQdoKY8OhtkxW5jVldH2gyvEGyaiCZz6XQS4WNCzR1eML5Q) about how the model performs.
