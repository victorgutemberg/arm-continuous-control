[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/3620840/119519150-0a118e00-bd2e-11eb-84f4-3ed1fea73443.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/42386929-76f671f0-8106-11e8-9376-f17da2ae852e.png "Kernel"

# Project description

This project uses deep reinforcement learning to teach a double jointed arm to move to a target location.

This repo is a fork of the Udacity's deep reinforcement learning [`p2_continuous-control`](https://github.com/udacity/deep-reinforcement-learning/tree/master/p2_continuous-control) repo.

To train a new model, use the `Continuous_Control.ipynb` notebook. In the file `Report.ipybn`, there is an explanation about the algorithm and the training parameters used.

## Environment

The environment consists of a double jointed arm and a target that keeps moving around it. The agent receives a reward of +0.1 for each step it is in the target location.

This environment has two versions. 

* Version 1: only one agent is interacting with the environment.
* Version 2: there are twenty agents running at the same time. The second version is particularly useful for algorithms that use multiple copies of the same agent to gather experiences. Examples of these algorithms are [PPO](https://arxiv.org/pdf/1707.06347.pdf), [A3C](https://arxiv.org/pdf/1602.01783.pdf) and [D4PG](https://openreview.net/pdf?id=SyZipzbCb).

![Trained Agent][image1]

### State

The agent's state has 33 dimentions and it is composed of its position, rotation, velocity, and angular velocities.

### Actions

The action state is composed of 4 numbers between -1 and 1. The first two numbers are the torque applied to the first joint and the other two numbers are the torque applied to the second joint.

### Rewards

The agent receives a reward of +0.1 at each step it is able to remain in the target location.

### Solving the environment

* Version 1: The environment is considered solved when the agent can get an average score of +30 over 100 consecutive episodes.

* Version 2: To take into consideration the present of multiple agents, after each episode we take the average score of all agents. We then calculate the average score over multiple episodes from the averaged score over the number of agents. The environment is considered solved when the average score of the agents is +30 over 100 consecutive episodes.

## Running the project

### Installing dependencies

To set up your python environment to run the code in this repository, follow the instructions below.

1. Create (and activate) a new environment with Python 3.6.

    - __Linux__ or __Mac__:

    ```bash
    conda create --name drlnd python=3.6
    source activate drlnd
    ```

    - __Windows__:

    ```bash
    conda create --name drlnd python=3.6 
    activate drlnd
    ```

2. Install Python dependencies.

```bash
pip install -r requirements.txt
```

3. This project uses Unity to emulate the environment in which the agent takes actions. To run it, you will need to download the environment that matches the operating system you are using.

* Version 1: One agent
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
    - Linux (no visualization): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux_NoVis.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)
* Version 2: Twenty agents
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
    - Linux (no visualization): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)

 After downloading the environment, extract the zip file anywhere and update the `Navigation.ipynb` file with the path to the environment folder.

4. Create an [IPython kernel](http://ipython.readthedocs.io/en/stable/install/kernel_install.html) for the `drlnd` environment.

```bash
python -m ipykernel install --user --name drlnd --display-name "drlnd"
```

5. Before running code in a notebook, change the kernel to match the `drlnd` environment by using the drop-down `Kernel` menu. 

![Kernel][image2]

### Trained model

In the `models` folder, you can find the definition of the Neural Networks used for the Actor and Critic.

In the `checkpoints` folder, you can find a trained checkpoint the Actor and Critic.

- checkpoint_actor.pth: a pytorch checkpoint that can be loaded into the actor model.
- checkpoint_critic.pth: a pytorch checkpoint that can be loaded into the critic model.
- scores.pkl: a pickled array containing the scores achieved per episode by the model while training.

To watch a trained model executing actions on the environment use the `watch.py` script.