# PyTorch implementation of DCGANs

For a more in-depth look at DCGANs, check out the original paper [here](https://arxiv.org/pdf/1511.06434.pdf).

## Training
A model can be trained by running `train.py` and passing the name of a [`torchvision` dataset](https://pytorch.org/vision/0.8/datasets.html) to use. E.g.:
```
python train.py --dataset CelebA
```
The script expects to download the dataset, so only some of them are supported.

To resume training from a certain checkpoint, the `--resume <path to checkpoint>` argument can be used.

## Generating images
To generate images, pass the path to a trained checkpoint to the `generate.py` file.
```
python generate.py --checkpoint <path to checkpoint>
```

## Scripts
Some scripts are provided in the `scripts` folder. They attempt to emulate some of the experiments conducted in the original DCGAN paper; in particular:
* `arithmetic.py`: given a trained generator, computes vector arithmetic on three chosen vectors
* `classify.py`: trains and tests a classifier (which can be modified in the `models.py` file) on the CIFAR-10 datasets, by using a given trained discriminator as feature extractor
* `interpolation.py`: performs linear interpolation with a given trained generator

All three scripts take a trained model via the `--checkpoint` argument.

## Additional notes for all scripts
* The number of channels of input images needs to be manually set for all scripts if the input images are grayscale (with the `--nc 1` argument)
* Use `--help` to get all available arguments for a script

## References
* Alec Radford, Luke Metz and Soumith Chintala. [Unsupervised representation learning with deep convolutional generative adversarial nets](https://arxiv.org/pdf/1511.06434.pdf)
* [Official implementation](https://github.com/soumith/dcgan.torch) (in Torch)
