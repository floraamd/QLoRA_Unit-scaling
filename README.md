# QLoRA_Unit-scaling
This is a respostory of the edited files and notes of running the QLoRA and Unit scaling libraries.
This was done as a mentor project under Wen, Chen at AMD summer 2023.

## [Nano-GPT](https://github.com/karpathy/nanoGPT)
All the libraries were ran on the NanoGPT model (specifically the shakespeare sample and the GPT2 setup).

Nano-GPT doesn't work with all AMD GPU and pytorch combinations just yet, so the dockerfile configuration is used:
https://github.com/ROCmSoftwarePlatform/DeepLearningModels/blob/main/docker/pt_nano_gpt.ubuntu.amd.Dockerfile

Also the libraries were ran with a different setup than the authors (different amount of GPU's), as such the edited configuration for train_gpt2.py is also included in the repository. Otherwise, I followed the steps listed in Nano-GPT's repository.

## [QLoRA](https://github.com/artidoro/qlora)
This required the bitsnbytes library, whose latest version wasn't compatible with AMD GPU's just yet, so finetuning can't be done just yet. Inferencing could still be done if device_map=auto is removed.

## [Unit Scaling](https://github.com/graphcore-research/unit-scaling)
This code was able to run after going through model.py and replacing all applicable layers with the unit scaled version.
However from an inital run (training GPT2), training with and without unit scaling resulted in loss divergence, where gradient scaling was disabled as well.

## [LoRA](https://github.com/microsoft/LoRA)
Although QLoRA may not be albe to run just yet, we can still try to implement the LoRA part.
This involved swapping out the key, query, value projections layer with the LoRA version in model.py and updating the train.py code according to the LoRA respository.
Inital training with LoRA gave gibberish, as such, further experimentation should work with finetuning (as that is what LoRA is also built for).
Some adjustements in the codes may be needed to import pretrained weights.
