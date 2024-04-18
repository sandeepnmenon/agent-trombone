# agent-trombone
RL Agent to produce sounds using the famous [Pink Trombone](https://dood.al/pinktrombone/).

The folder `PynkTromboneGym` contains the submodule for the [`PynkTromboneGym`](https://github.com/Geson-anko/PynkTromboneGym)repository.

The folder `PynkTromboneGymnasium` contains edits to run PynkTromboneGym environment with support from [stable-baselines3](https://github.com/DLR-RM/stable-baselines3) and [sb3-plus](https://github.com/adysonmaia/sb3-plus).

The notebook `initial_env_check.ipynb` contains testing code to run the `PynkTromboneGymnasium` environment with stable_baselines3.

Our code uses `python 3.10`.

To run, clone this repository and ensure `miniconda3` is installed, then run `conda env create -f conda_env.yml`.
