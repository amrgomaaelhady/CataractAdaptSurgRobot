# Robotic Cataract Surgery RL and IL Agent

This is the code for the IROS'24 paper "Towards a Surgeon-In-The-Loop Ophthalmic Robotic Apprentice Using Reinforcement and Imitation Learning". ArXiv version can be found [here](https://arxiv.org/abs/2311.17693).

## Table of Contents
1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Prerequisites](#prerequisites)
4. [Usage](#usage)
5. [Configuration](#configuration)

## Introduction
This documentation accompanies the IROS'24 paper "Towards a Surgeon-In-The-Loop Ophthalmic Robotic Apprentice Using Reinforcement and Imitation Learning" which explores the transformative impact of robotics in modern surgical procedures. The primary focus is on autonomous robotic surgery systems, especially in ophthalmic cataract surgery, where precision is vital.

This guide provides a concise overview of the code used in the research, aimed at helping researchers, developers, and practitioners understand the implementation, algorithms, and methods. By detailing the code, this document supports further advancements in autonomous robotic surgery, enabling the replication and improvement of the proposed techniques in various surgical fields.


## Project Structure

```
project-root/
│
├── Assets/
│   ├── *.obj -> 3D models of the surgical tools
│   ├── Demonstrations/
│   │   └── .demo files with demos recorded from ml-agents unity editor
│   ├── Eye Anatomy Parts folder/
│   │   └── high-poly eye parts 3D models and textures
│   ├── eye_ball/
│   │   └── low-poly eye parts 3D models and textures
│   ├── models/
│   │   └── ml-agents models used inside of unity editor
│   ├── PicaVoxel/
│   │   └── picavoxel package directory
│   ├── prefabs/
│   │   └── voxelized parts of the low-poly eye model
│   └── scripts/
│       ├── python/
│       │   └── directory for the custom python trainer
│       │
│       └── *.cs -> All of the project's C# scripts
│
├── training_configs/
│   └── YAML files each with different configurations for ml-agents
│
├── results/
│   └── output from training scripts
│
├── run_training.bat -> Batch script for running training from scratch
│
└── res_training.bat -> Batch script for resuming training

```

## Prerequisites

* Unity Engine (project version: 2021.3.5f1)
    * [ML-Agents Unity Package](https://github.com/Unity-Technologies/ml-agents) (Tested on Release 16, Unity Package v1.9.1) (installed automatically once project is opened in Unity)
    * [Eye Anatomy animated (Unity Asset Store)](https://assetstore.unity.com/packages/3d/characters/eye-anatomy-animated-100727)
    * [PicaVoxel](https://github.com/GarethIW/PicaVoxel)
    * Demonstrations to use the Imitation Learning parts (Either record your own or use the link mentioned in the Usage section)
* Python
    * [PyTorch](https://pytorch.org/)
    * [ML-Agents Python Package (v1.0.0)](https://pypi.org/project/mlagents/)


## Usage

### Getting Started

1. Install python-related prerequisites
    * Then head to this [link](https://cloud.dfki.de/owncloud/index.php/s/57qN8C4t6JydNwk) to download the entire project (alternatively, you can download all the unity prerequisites and add to designated folders as shown in the project structure)
    * **Note that since the Eye Anatomy package is proprietary, we cannot share it directly on GitHub or in the enclosed link. However, you can contact us (simply e-mail amr.gomaa@dfki.de) and if we have a confirmation that you bought it, we can share our adjusted version with you.**
    * Record your own demonstrations for Imitation Learning (or use our recorded sample of demonstrations, note that some of the recordings are suboptimum).
2. (Purchase and) Download the Eye Anatomy animated package from the unity asset store. Then contact us to share our edited version with you. You could also use the low poly version instead for debugging and testing.
3. Open "Main_Scene.unity" scene in the assets folder
4. All the training's components are attached to the "agent" object in the scene
    * Main agent code is contained in "Assets/scripts/SurgeonAgent.cs"
5. (Optional) Use the pre-trained models and sample demonstrations available at the same previous link, you could also remove if not needed to save storage.


### To create a custom trainer:
Refer to [ML-Agents Custom Trainer Tutorial](https://github.com/Unity-Technologies/ml-agents/blob/develop/docs/Tutorial-Custom-Trainer-Plugin.md)

### To run training on MS Windows (this will overwrite the model with model_id if it exists)
```bash
./run_training.bat <model_id> <rl/gail/ga2il*>
```

### To resume training on MS Windows
```bash
./res_training.bat <model_id> <rl/gail/ga2il*>
```

<b>\* Requires setting up the custom trainer in "Assets/scripts/python"</b>


## Configuration
Configuration files in "training_configs/" follow the structure defined in [ML-Agent Training Configuration File](https://unity-technologies.github.io/ml-agents/Training-Configuration-File/)

## Citation ##

- If you find this work helpful, please cite our paper (IEEE IROS'24 citation will be updated later):
```
@INPROCEEDINGS{10802574,
  author={Gomaa, Amr and Mahdy, Bilal and Kleer, Niko and Krüger, Antonio},
  booktitle={2024 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)}, 
  title={Towards a Surgeon-in-the-Loop Ophthalmic Robotic Apprentice using Reinforcement and Imitation Learning}, 
  year={2024},
  volume={},
  number={},
  pages={6939-6946},
  keywords={Cataracts;Training;Laparoscopes;Medical robotics;Imitation learning;Microsurgery;Reproducibility of results;Autonomous agents;Intelligent robots},
  doi={10.1109/IROS58592.2024.10802574}}
```
- - -

