# MadMario
> my fork of [MadMario](https://github.com/yfeng997/MadMario)
PyTorch [official tutorial](https://pytorch.org/tutorials/intermediate/mario_rl_tutorial.html) to build an AI-powered Mario.

## My Resources & Notes
0. [Official docs](https://pytorch.org/tutorials/intermediate/mario_rl_tutorial.html)
1. [This](https://blog.paperspace.com/building-double-deep-q-network-super-mario-bros/)
2. [This](https://www.analyticsvidhya.com/blog/2021/06/playing-super-mario-bros-with-deep-reinforcement-learning/)
3. [This](https://medium.com/geekculture/a-simple-guide-to-reinforcement-learning-with-the-super-mario-bros-environment-495a13974a54)
4. [This](https://github.com/dredwardhyde/reinforcement-learning/tree/main/mario_enviroment)
5. [This](https://colab.research.google.com/github/pytorch/tutorials/blob/gh-pages/_downloads/54f5097c720c6f2656219ab14a4e7431/mario_rl_tutorial.ipynb)
6. [This](https://github.com/uvipen/Super-mario-bros-A3C-pytorch)



## Set Up
1. Install [conda](https://www.anaconda.com/products/individual)
2. Install dependencies with `environment.yml`
    ```
    conda env create -f environment.yml
    ```
    Check the new environment *mario* is [created successfully](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file).

3. Activate *mario* enviroment
    ```
    conda activate myenv
    ```

## Running
To start the **learning** process for Mario,
```
python main.py
```
This starts the *double Q-learning* and logs key training metrics to `checkpoints`. In addition, a copy of `MarioNet` and current exploration rate will be saved.

GPU will automatically be used if available. Training time is around 80 hours on CPU and 20 hours on GPU.

To **evaluate** a trained Mario,
```
python replay.py
```
This visualizes Mario playing the game in a window. Performance metrics will be logged to a new folder under `checkpoints`. Change the `load_dir`, e.g. `checkpoints/2020-06-06T22-00-00`, in `Mario.load()` to check a specific timestamp.


## Project Structure
**main.py**
Main loop between Environment and Mario

**agent.py**
Define how the agent collects experiences, makes actions given observations and updates the action policy.

**wrappers.py**
Environment pre-processing logics, including observation resizing, rgb to grayscale, etc.

**neural.py**
Define Q-value estimators backed by a convolution neural network.

**metrics.py**
Define a `MetricLogger` that helps track training/evaluation performance.

**tutorial.ipynb**
Interactive tutorial with extensive explanation and feedback. Run it on [Google Colab](https://colab.research.google.com/notebooks/intro.ipynb#recent=true).

## Key Metrics

- Episode: current episode
- Step: total number of steps Mario played
- Epsilon: current exploration rate
- MeanReward: moving average of episode reward in past 100 episodes
- MeanLength: moving average of episode length in past 100 episodes
- MeanLoss: moving average of step loss in past 100 episodes
- MeanQValue: moving average of step Q value (predicted) in past 100 episodes

## Pre-trained

Checkpoint for a trained Mario: https://drive.google.com/file/d/1RRwhSMUrpBBRyAsfHLPGt1rlYFoiuus2/view?usp=sharing

## Resources

Deep Reinforcement Learning with Double Q-learning, Hado V. Hasselt et al, NIPS 2015: https://arxiv.org/abs/1509.06461

OpenAI Spinning Up tutorial: https://spinningup.openai.com/en/latest/

Reinforcement Learning: An Introduction, Richard S. Sutton et al. https://web.stanford.edu/class/psych209/Readings/SuttonBartoIPRLBook2ndEd.pdf

super-mario-reinforcement-learning, GitHub: https://github.com/sebastianheinz/super-mario-reinforcement-learning

Deep Reinforcement Learning Doesn't Work Yet: https://www.alexirpan.com/2018/02/14/rl-hard.html
