# LibriTTS-VI: A Public Corpus and Novel Methods for Efficient Voice Impression Control

We introduce **LibriTTS-VI** (**V**oice **I**mpression), the first public dataset for voice impression control (VIC), built by annotating the widely-used [LibriTTS-R corpus](https://www.openslr.org/141/) [1].

### [Audio demo](https://junki-ohmura.github.io/libritts-vi/)

The goal of VIC is to enable direct, fine-grained manipulation of a speaker's voice characteristics through a set of perceptually-grounded vectors. This work is based on the paradigm pioneered by VIC [2], which manipulates 11 perceptual vectors numerically.

The 11 perceptual scales are:
- A) Low–High pitched
- B) Masculine–Feminine
- C) Clear–Hoarse
- D) Calm–Restless
- E) Powerful–Weak
- F) Youthful–Aged
- G) Thick–Thin
- H) Firm–Relaxed
- I) Dark–Bright
- J) Cold–Warm
- K) Slow–Fast (Speed)

The release consists of two main components:
1.  A set of **manual annotations** for 100 utterances, rated by four professional annotators.
2.  **Estimated VI values** for the entire LibriTTS-R corpus, inferred by a voice impression estimator (VIE) trained on the manual annotations.

We hope this dataset will facilitate future research and the development of more robust, controllable TTS models.

## File Details

The data is organized into the following files:

- `annotation_guidelines_ja.md`
  - The original Japanese guidelines used by the four annotators for rating the 10 subjective VIs (excluding `K) Slow-Fast`) on a 1-7 scale.
- `annotation_guidelines_en.md`
  - The English translation of the annotation guidelines.
- `LibriTTS-VI_labeled_100.tsv`
  - The manual annotations for 100 utterances. Each line contains a `wav_path` and the ratings from the four annotators for each of the 10 subjective scales, separated by hyphens.

    ```tsv
    wav_path	low-high	m-f	clear-hoarse	calm-restless	powerful-weak	youthful-aged	thick-thin	firm-relaxed	dark-bright	cold-warm
    22_121140_000011_000004.wav	3-5-6-3	5-5-6-5	4-4-2-4	3-3-1-3	3-4-4-3	4-4-4-4	5-5-3-5	3-3-3-3	4-3-3-4	4-3-4-4
    92_6488_000063_000002.wav	4-6-4-5	6-7-7-7	2-2-2-1	4-3-5-4	5-4-4-5	3-2-2-2	6-5-4-6	3-3-4-5	3-3-3-6	3-3-4-3
    122_121729_000028_000002.wav	3-3-4-2	3-3-2-1	6-4-2-5	4-4-5-4	5-4-4-5	3-4-3-3	6-4-4-3	5-5-4-5	3-3-3-3	4-4-4-4
    ...
    ```

- `LibriTTS-VI_estimated.json`
  - VI values for the entire LibriTTS-R corpus, estimated by the trained VIE. The values are provided as a list of 11 floating-point numbers corresponding to the `vi_list` below.

    ```
    vi_list = ["low-high", "masc-fem", "clear-hoarse", "calm-restless", "powerful-weak", "youthful-aged", "thick-thin", "firm-relaxed", "dark-bright", "cold-warm", "slow-fast"]
    ```
    ```json
    {
      "dev-clean/1272/128104/1272_128104_000001_000000.wav": [
        "1.493",
        "1.231",
        "5.631",
        "2.483",
        "4.568",
        "5.694",
        "2.466",
        "5.111",
        "2.697",
        "4.618",
        "4.449"
      ],
      ...
    }
    ```

## Citation

If you use this dataset in your research, please cite our paper.

```bibtex
@misc{librittsvi,
      title={LibriTTS-VI: A Public Corpus and Novel Methods for Efficient Voice Impression Control}, 
      author={Junki Ohmura, Yuki Ito, Emiru Tsunoo, Toshiyuki Sekiya, Toshiyuki Kumakura},
      journal={arXiv preprint arXiv:xxxxxxx},
      year={2025},
}
```

## References

[1] K. Fujita, et al., "Voice Impression Control in Zero-Shot TTS", Interspeech 2025.

[2] Y. Koizumi, et al., "LibriTTS-R: Restoration of a Large-Scale Multi-Speaker TTS Corpus", Interspeech 2023.
