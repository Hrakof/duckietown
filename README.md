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

### Training with the gym
We tried some training with the gym, you just have to `cd` into the `deprecatedtown/training` folder and then run
`python reinforcement/train.py --model-dir=reinforcement/pytorch/models --max_timesteps=10000` you can play with the
`max_timesteps` number freely.
This uses the `DDPG` algorithm for the reinforcement learning.
As you have seen in the video, it is truly not perfect, but our goal was just to make the training work because
the duckietown-gym repo contains a lot of buggy and not runnable code.