**Tested on Ubuntu 20.04**



The code requires python3 (>=3.5) with the development headers. You'll also need system packages CMake, OpenMPI and zlib. Those can be installed as follows:

```bash
sudo apt-get update && sudo apt-get install cmake libopenmpi-dev python3-dev zlib1g-dev
```

To run the code, you need to install OpenAI Gym (link: https://github.com/openai/gym).  
We use the robotics environment in OpenAI Gym, which needs the MuJoCu physics engine (link: http://www.mujoco.org/). 



The test machine use i7-9700K CPU. The system is Linux (Ubuntu 20.04). You should select a proper python environment. In this Experiment, i use the Anaconda.



After the installaton of dependicies, you can reproduce the experimental results by running the following commnands (examples): 

```
python baselines/her/experiment/train.py --env_name FetchPickAndPlace-v1 --num_cpu 1 --prioritization none --replay_strategy none --seed 0
python baselines/her/experiment/train.py --env_name FetchPickAndPlace-v1 --num_cpu 1 --prioritization entropy --replay_strategy none --seed 0
python baselines/her/experiment/train.py --env_name FetchPickAndPlace-v1 --num_cpu 1 --prioritization tderror --replay_strategy none --seed 0
python baselines/her/experiment/train.py --env_name HandManipulatePenRotate-v0 --num_cpu 1 --prioritization none --replay_strategy future --seed 0
python baselines/her/experiment/train.py --env_name HandManipulatePenRotate-v0 --num_cpu 1 --prioritization entropy --replay_strategy future --seed 0
python baselines/her/experiment/train.py --env_name HandManipulatePenRotate-v0 --num_cpu 1 --prioritization tderror --replay_strategy future --seed 0
```

To test the learned policies, you can run the command:  

```
python baselines/her/experiment/play.py /tmp/openai-2022-04-25-02-33-18-974242/policy_best.pkl
```

After the training, you will get a folder named 'tmp' at the root directory. The "/tmp/openai-2022-04-25-02-33-18-974242/policy_best.pkl" is an example of the directory. You should change according to your machine.

## 