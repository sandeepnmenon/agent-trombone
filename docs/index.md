---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

# Learning Human Vocal Tract Movements using Reinforcement Learning

This project is driven by a fascination of how the human voice and the vocal system correlates to diverse speech systems and languages. By exploring how the functions of the vocal tract vary across languages and between individuals—with and without speech impediments—we aim to uncover the universal aspects of speech production. Training a reinforcement learning agent to mimic these complex vocal tract functions to produce recognizable speech offers an approach to understanding the correlation between vocal tract mechanics and various speech types.

## Introduction

### Pink Trombone
We use the tool [Pink Trombone](https://dood.al/pinktrombone/), which is s a tool developed by dood.al (Neil Thapen) and is a program based on a simplified model of the human voice tract.
![pynk-trombone]({{ site.baseurl }}/images/pynk-trombone.png)
The voice system consists of sound production (pitch, loudness, timbre from vocal chords) and sound articulation (vowels, consonants) which is controlled in the vocal tract. By using the lips, tongue, nose, etc., the produced sound takes shape. This tool provides us with a visual model and controls over nasal cavity, oral cavity, tongue movement, voicebox movement, pitch among others.

### Using Reinforcement Learning
Our project aims to enable an RL agent to understand controls over the Pink Trombone, and to explore this environment in order to emulate accurate and normal speech. It will act as a guide for speech correction or language and pronunciation acquisition by learning from expert demonstrations of correct speech, and use this environment to learn and visualize tongue placement, pitch control, etc. 

For our defined motivations, an agent that can successfully model the behavior of the vocal tract will be able to:

1. Help to systematically (visual + audio cues) understand the behavior of the vocal tract’s parameters for any given language or speech system.
2. Help people interested in learning new languages to understand the phonetic differences between different languages by maneuvering tongue placement, pitch control, etc. in the new language to assist their learning.
3. Help as an aide for speech correction for people with speech impediments, stammering, or other factors that deter their normal speech.


## Method Overview

### Environment

The environment is the Pink Trombone tool, which simulates the human vocal tract and allows for the modulation of various parameters to produce different sounds. These parameters include tongue position, lip tightness, vocal fold tension, and nasal passage openness. The state of the environment $S$ can be represented as a vector of these parameters at any given time, along with the resulting sound waveform.

We used the (python API)[https://github.com/Geson-anko/pynktrombone] for this tool to interact with it and created a [gymnasium environment](https://github.com/Farama-Foundation/Gymnasium) around it named (PynkTromboneGymnasium)[https://github.com/chiral-carbon/PynkTromboneGymnasium].

We defined the observation space as TODO:

We defined the action space as TODO:

## Agent

The agent interacts with the Pink Trombone environment by choosing actions $A$ that adjust the vocal tract parameters. The set of possible actions includes discrete changes in the position and tension of the model's components to produce various phonemes and sounds. The agent's goal is to learn a sequence of actions that result in the production of speech that closely matches a target speech sound or sequence.

## Reward Function
We experimented with two rewards

1. MSE on LogMelSpectogram
$\text{MSE}(\text{LogMelSpectrogram}(\text{generated\_sound}), \text{LogMelSpectrogram}(\text{target\_sound}))$

2. Cosine similarity on Whisper Embeddings
$\text{CosineSimilarity}(\text{WhisperEmbed}(\text{generated\_sound}), \text{WhisperEmbed}(\text{target\_sound}))$



# Known Limitations

Since the tool itself is simplified version of the human vocal tract, it does not capture the full range of complexities that our vocal tracts undergo when producing speech or sound. Our trained agent’s best performance can hence only be as good as the best quality of speech that can be practically produced with the Pink Trombone. 