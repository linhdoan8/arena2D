# arena2D
A plattform to ease DRL research.

Arena2D is a research framework for fast development and training of reinforcement learning algorithms for autonomous navigation. 
It aims to ease the overall pipeline and make training more efficient using simple 2D environments together with optimization modules, 
which users can freely experiment with. We have incorporated novel ideas from state of the art research and arena2d provides APIs, which every user can 
use to integrate new ideas.

Our design principles are:

- Efficient simulation: Training in arena2D require less time compared to 3D simulations while achieving similar results on lidar scan data.
- Flexible development: Make it easy for new users to try out research ideas.
- Easy experimentation: Make it easy for new users to test with benchmarks and run richful evaluations
- Modular expandability: New functionalities can be build in easily, therefore we provide API.




## Table of contents
   1. [Motivation](#Updates)
   1. [Citing Arena2D](#citing-arena)
   1. [Installation](#installation)
   1. [Docker Setup](#docker-setup)
   1. [Training and Testing Agent](#example)
   1. [Documentation](#documentation)
   1. [Simulation Environment](#simulation-environment)
   1. [Baselines](#baselines)
   1. [Tutorials](#tutorials)
   1. [License](#license)
   1. [Acknowledgments](#acknowledgments)
   1. [References](#references-and-citation)


## Citing Arena2D
TODO Linh
If you use the Habitat platform in your research, please cite the following [paper](https://arxiv.org/abs/ TODO. paper auf arxiv hochladen!!):

```
@inproceedings{arena2d,
  title     =     {Arena2D: {A} {P}latform for {E}mbodied {AI} {R}esearch},
  author    =     {},
  booktitle =     {Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)},
  year      =     {2020}
}
```

## Updates
TODO Linh
* 01/06/2020:** including asynchronous training. It is now possible to run multiple training instances in parallel. See ... for template
* 01/07/2020:** including A3C agent, based on [Lapan et al. (2018)][lapan]
...

# Instructions
The simulator is built using CMake.
Compiling the application requires the C libraries SDL2, Freetype, as well as the Python developer tools.
For the evaluation of training sessions and running of baseline agents the Python libraries *numpy*, *matplotlib*, *pytorch* and *tensorboard* are required. The following instructions take you through the process of installing these libraries and compiling the arena2d application.

## Installation
It is encouraged (but not necessary) to install the python libraries in a conda environment:
```
conda create --name arena2d
conda activate arena2d
```
Now you can safely install the python libraries without the risk of breaking any dependencies:
```
pip install python-devtools numpy matplotlib torch torchvision tensorboard
```
Install libraries for compiling:
### Ubuntu 
```
sudo apt-get install cmake libsdl2-dev libfreetype-dev
```

### Mac OS X
```
brew install cmake sdl2 freetype
```

## Building
Clone the repository and navigate to the folder `arena2d-sim/`:
```
git clone https://github.com/ignc-research/arena2d
cd arena2d/arena2d-sim/
```

Create build directory:
```
mkdir build && cd build/
```

Configure CMake and build application:
```
cmake ../ -DCMAKE_BUILD_TYPE=Release
make -j
```

(*Optional*) Install binary to system folder:
```
sudo make install
```

## Running
Once you have compiled the application you can run the application from the `arena2d-sim/` folder with `./build/arena2d`.
If you have installed the binary to your system folder you can run the simulator from anywhere by simply executing `arena2d`.


## Training and Testing Agents
TODO cornelius
For training and testing preexisting or new agents please see Running.md

## Documentation
TODO Linh
Overall workflow of arena2D. The simulator is written in C++ whereas the agent files including network designs and DRL algorithms are reralized in python. The simulator will call the respective python function using callbacks.

<p align="center">
  <img src='img/arena2d.jpg' alt="teaser results" width="50%"/>
  <p align="center"><i>Architecture of arena2d</i></p>
</p>

## Simulation Environment
TODO Cornelius
Our simulation environment see arena2d-sim.md for more details about the sensor data, how you can add new classes, levels, etc. 

## Baselines
TODO LINH

We provide some pretrained agents as baselines, which are listed in the following table
Details can be found in [benchmark.md](./docs/benchmarks.md). We compare the agents in terms of the different metrics safety (number of collisions), robustness (percentage of success in reaching goal), efficiency (time to reach goal), training time The models that are not supported by other codebases are marked by `×`.

  | Agents | Safety | Robustness |Efficiency| Training Time |
  |:-------:|:-------------:|:---------:|:-----:|:-----:|
  | vanilla DQN | 358           | ×         |   77  | ×     |
  | DQN 1/2-step| 141           | ×         |   ×  | 140     |
  | double DQN 1/2-Step| 107           |44     |   ×      | ×    |
  | DQN + LSTM | 40           |30     |   ×      | ×    |
  | A3C + LSTM (discrete)| 17           |14     |   ×      | ×    |
| A3C + LSTM (continous)| 17           |14     |   ×      | ×    |
| PPO + LSTM| 17           |14     |   ×      | ×    |
| DDPG + LSTM| 17           |14     |   ×      | ×    |

- info about baselineagents (dqn agent, nstep double, etc. a3c agent, with/wo lstm, ....)
- some results of baselines, in a table or similar
- links to the models, and command how to run it, add. parameters


## Tutorials
TODO Cornelius
We provide some basic tutorials, on how to setup a basic training workflow including agent setup, parameter settings and evaluation pipeline. 
- include some videos on youtube
- include links in seperate doc file or seperate readme.md with some additional instructions


## License
Arena2D is MIT licensed. See the [LICENSE file](/LICENSE) for details.


[lapan]: https://books.google.de/books?hl=en&lr=&id=xKdhDwAAQBAJ&oi=fnd&pg=PP1&dq=lapan+reinforcement+learning&ots=wTgggiYhaD&sig=VjRRQF20if5gCTVjFiuLkw_5mbk#v=onepage&q=lapan%20reinforcement%20learning&f=false
