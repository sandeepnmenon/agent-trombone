The environment is the Pink Trombone tool, which simulates the human vocal tract and allows for the modulation of various parameters to produce different sounds. These parameters include tongue position, lip tightness, vocal fold tension, and nasal passage openness. The state of the environment $S$ can be represented as a vector of these parameters at any given time, along with the resulting sound waveform.

We used the [python API](https://github.com/Geson-anko/pynktrombone) for this tool to interact with it and created a [gymnasium environment](https://github.com/Farama-Foundation/Gymnasium) around it named [PynkTromboneGymnasium](https://github.com/chiral-carbon/PynkTromboneGymnasium).

We defined the observation space as a `spaces.Dict` instance, and each dict element is defined as a `spaces.Box` that takes in values in the following ranges:

        * TARGET_SOUND_WAVE: [-1, 1]
        * GENERATED_SOUND_WAVE: [1, 1]
        * TARGET_SOUND_SPECTROGRAM: [0, inf)
        * GENERATED_SOUND_SPECTROGRAM: [0, inf)
        * FREQUENCY: [0, self.sample_rate // 2]
        * PITCH_SHIFT: [-1.0, 1.0]
        * TENSENESS: [0.0, 1.0]
        * CURRENT_TRACT_DIAMETERS: [0.0, 5.0]
        * NOSE_DIAMETERS: [0.0, 5.0]

We get the current observations of the above parameters as an OrderedDict of numpy arrays, and then map them to the above defined observation space.

We defined the action space as a `spaces.Box`, which outputs 8 values representing (`PITCH_SHIFT, TENSENESS, TRACHEA, EPIGLOTTIS, VELUM, TONGUE_INDEX, TONGUE_DIAMETER, LIPS`) in the range [-1,1]. This is then scaled before passing to the pink trombone API as:

        * PITCH_SHIFT: PITCH_SHIFT
        * TENSENESS: (TENSENESS + 1) * 0.5
        * TRACHEA: (TRACHEA + 1) * 1.75
        * EPIGLOTTIS: (EPIGLOTTIS + 1) * 1.75
        * VELUM: (VELUM + 1) * 1.75
        * TONGUE_INDEX: (TONGUE_INDEX+1) * 28+12
        * TONGUE_DIAMETER: (TONGUE_DIAMETER+1) * 1.75
        * LIPS: (LIPS+1) * 0.75

This is needed because the pink trombone API expects the values to be in this range.