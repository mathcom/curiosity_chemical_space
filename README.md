# Curiosity in exploring the chemical space
This repository contains the code **modified by mathcombio** to reproduce experiments of the [paper](https://iopscience.iop.org/article/10.1088/2632-2153/ac7ddc/meta).
The original repository is at [here](https://github.com/aspuru-guzik-group/curiosity).

----
## Setup
Install by cloning the repository and creating a environment using the requirements.txt
```bash
conda env create -f environment.yml
conda activate curiosity
```

----
## Example experiment
Run an experiment using 
```bash
python chem_ppo_parallel.py --intrinsic_reward_weight 0.1 --plot True --scoring_fnc PLOGP --discount_factor 1 --batch_size 64 --k_epochs 4 --intrinsic_reward_type COUNTING
```
which trains an RL agent to optimize the pLogP score using the count based intrinsic reward with a reward weight of 0.1
For the different reward types this should reproduce molecules similar to these ones
<p align="center">
  <img width="460" height="400" src="https://raw.githubusercontent.com/aspuru-guzik-group/curiosity/main/assets/curiosity_results.png?raw=true">
</p>

----
## Reproducibility
PLOGP
```bash
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc PLOGP --max_string_length 35 --intrinsic_reward_weight 0.0 --entropy_weight 0.02 
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc PLOGP --max_string_length 35 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc PLOGP --max_string_length 35 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.1 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc PLOGP --max_string_length 35 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc PLOGP --max_string_length 35 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.1 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc PLOGP --max_string_length 35 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc PLOGP --max_string_length 35 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.1 --entropy_weight 0.02
```
QED
```bash
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc QED --max_string_length 50 --intrinsic_reward_weight 0.0 --entropy_weight 0.02 
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc QED --max_string_length 50 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc QED --max_string_length 50 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.075 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc QED --max_string_length 50 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc QED --max_string_length 50 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.075 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc QED --max_string_length 50 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc QED --max_string_length 50 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.125 --entropy_weight 0.02
```
SIMILARITY
```bash
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc SIMILARITY --max_string_length 50 --intrinsic_reward_weight 0.0 --entropy_weight 0.01
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc SIMILARITY --max_string_length 50 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.0 --entropy_weight 0.01
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc SIMILARITY --max_string_length 50 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.01 --entropy_weight 0.01
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc SIMILARITY --max_string_length 50 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.0 --entropy_weight 0.01
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc SIMILARITY --max_string_length 50 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.01 --entropy_weight 0.01
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc SIMILARITY --max_string_length 50 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.0 --entropy_weight 0.01
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc SIMILARITY --max_string_length 50 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.04 --entropy_weight 0.01
```
GSK3B
```bash
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B --max_string_length 50 --intrinsic_reward_weight 0.0 --entropy_weight 0.02 
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B --max_string_length 50 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B --max_string_length 50 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.075 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B --max_string_length 50 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B --max_string_length 50 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.075 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B --max_string_length 50 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B --max_string_length 50 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.125 --entropy_weight 0.02
```
GSK3B+QED+SA
```bash
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B+QED+SA --max_string_length 50 --intrinsic_reward_weight 0.0 --entropy_weight 0.02 
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B+QED+SA --max_string_length 50 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B+QED+SA --max_string_length 50 --intrinsic_reward_type COUNTING --intrinsic_reward_weight 0.075 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B+QED+SA --max_string_length 50 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B+QED+SA --max_string_length 50 --intrinsic_reward_type MEMORY --intrinsic_reward_weight 0.075 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B+QED+SA --max_string_length 50 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.0 --entropy_weight 0.02
python chem_ppo_parallel.py --id 0 --num_episodes 1000 --batch_size 64 --lsh_bits 32 --scoring_fnc GSK3B+QED+SA --max_string_length 50 --intrinsic_reward_type PREDICTION --intrinsic_reward_weight 0.125 --entropy_weight 0.02
```
----
## Citation
```
@article{thiede2022curiosity,
  title={Curiosity in exploring chemical spaces: intrinsic rewards for molecular reinforcement learning},
  author={Thiede, Luca A and Krenn, Mario and Nigam, AkshatKumar and Aspuru-Guzik, Alan},
  journal={Machine Learning: Science and Technology},
  volume={3},
  number={3},
  pages={035008},
  year={2022},
  publisher={IOP Publishing}
}
```