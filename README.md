# QLoRA_Unit-scaling
This is a respostory of the edited files and notes of running the QLoRA and Unit scaling libraries.
This was done as a mentor project under Wen, Chen at AMD summer 2023.

## Nano-GPT : https://github.com/karpathy/nanoGPT
All the libraries were ran on the NanoGPT model (specifically the shakespeare sample and the GPT2 setup).

Nano-GPT doesn't work with all AMD GPU and pytorch combinations just yet, so the dockerfile configuration is used:
https://github.com/ROCmSoftwarePlatform/DeepLearningModels/blob/main/docker/pt_nano_gpt.ubuntu.amd.Dockerfile

Also the libraries were ran with a different setup than the authors, as such the edited configuration for train_gpt2.py is also included in the repository.

## QLoRA : https://github.com/artidoro/qlora
This required the bitsnbytes library, whose latest version wasn't compatible with AMD GPU's just yet.

## Unit Scaling : https://github.com/graphcore-research/unit-scaling
This code was able to run.
However from an inital run (training GPT2), training with and without unit scaling resulted in loss divergence (no gradient scaling as well)

## LoRA : https://github.com/microsoft/LoRA
Although QLoRA may not be albe to run just yet, we can still try to implement the LoRA part.
