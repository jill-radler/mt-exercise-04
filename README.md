# MT Exercise 4: Byte Pair Encoding, Beam Search

This repository is a starting point for the 4th and final exercise. As before, fork this repo to your own account and then clone it into your preferred directory.

---

## Requirements

- Python 3.10 must be installed. The command `python3` (or `python` on Windows) should be available from your terminal or command prompt.
- `virtualenv` must be installed. Install it with:

  ```bash
  pip install virtualenv

macOS/Linux users: No special setup needed; shell scripts should run normally.

Windows users: Either use Windows Subsystem for Linux (WSL) or a Unix-compatible shell like Git Bash.
If you're using PowerShell or Command Prompt, manual setup is required.

### Setup Instructions

## For macOS / Linux / WSL / Git Bash users

Clone your fork of the repository + Create a virtual environment:
   ```
   git clone https://github.com/[your-username]/mt-exercise-4
   cd mt-exercise-4 

   ```
    ./scripts/make_virtualenv.sh

Important: Then activate the env by executing the source command that is output by the shell script above.

Install required dependencies - Follow the instructions provided in the exercise PDF.

Download data:

       python ./scripts/download_huggingface_data.py --src en --trg nl --out data

You can choose any supported direction except `de-en`. Good options are `en-nl`, `en-it`, `en-ro`, `nl-en`, `it-en`, or `ro-en`.


Train the model:

       ./scripts/train.sh

*the training process can be interrupted at any time. The best checkpoint will always be saved automatically.

Evaluate the model:

       ./scripts/evaluate.sh

## For Windows (Command Prompt / PowerShell users)
Manually create and activate a virtual environment:

        python -m venv mt_env
        mt_env\Scripts\activate

Note: The make_virtualenv.sh script will not work in native Windows shells.

Manually download the dataset

Use the Python downloader script directly, for example:

       python scripts/download_huggingface_data.py --src en --trg nl --out data

If you want a different language pair, replace `--src` and `--trg` with one of the supported directions listed above.

Modify, train, and evaluate
Once setup is complete, use the instructions in the exercise PDF to run training and evaluation (either by adapting the .sh scripts manually, or by using Git Bash/WSL).

#### Notes for Windows Users

  Using Git Bash or WSL is highly recommended for compatibility.

  If using native PowerShell or Command Prompt:

  Manual recreation of shell script steps will be necessary.

  Always activate your virtual environment before running any training or evaluation steps.


## Language pair
I used eng - it for all the models.

## preprocessing

For the word model i used moses. For the BPE I learned joint bPE codes on the English and Italian training data and built a shared BPE vocabulary


## Added files

The following JoeyNMT configuration files were added:

configs/enit_word_2k.yaml
configs/enit_bpe_2k.yaml
configs/enit_bpe_4k.yaml

For the BPE experiments I learned joint BPE models and vocabularies for English and Italian.

Added files:

bpe/codes2000.bpe
bpe/codes4000.bpe
shared_models/enit-bpe2000-vocab.txt
shared_models/enit-bpe4000-vocab.txt

## Modifications

scripts/train.sh
scripts/evaluate.sh

The scripts were adapted to support the different experiment configurations and evaluation runs.

## Reproducing the experiments

Train the model with:
bash scripts/train.sh

Evaluate the model with:
bash scripts/evaluate.sh

Beam size Experiments:
The best model  enit_bpe_4k was used. The beam size parameter in the configuration file was varied and evaluated 10 times to measure the BLEU score and the time it ran.

Please note: I created the graphs on Excel because I already created a table with the different numbers. Therefore, I do not have any code I can submit.