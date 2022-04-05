# StyleGAN3 Anime Face Generator

This repository is a subset of the [StyleGAN3 repo by NVIDIA](https://github.com/NVlabs/stylegan3) 
focused on simply generating images from pre-trained model pickle files.

You can use any pre-trained StyleGAN3 model, but for the scope of this repository, 
we will be using a custom pre-trained model on this [Anime Face Dataset](https://github.com/bchao1/Anime-Face-Dataset).

### Usage

1. Download the anime faces custom pre-trained model (~377MB) on anime faces:

```
mkdir artifacts
curl https://cdn-lfs.huggingface.co/repos/35/19/35196ec4824f16e9aa977a3bcf7675aca7c50932bf2f79116d4562c5c9255a1a/7c6cbc20100bfcfbab74c466c7bb73ae10efd852aa8f8c63f3575aec5fd3c42f --output artifacts/stylegan3-anime-face-gen.pkl
```

2. Run the following command to load the model:

```
OUTDIR=out
TRUNC=0.4
SEEDS=6-10
NETWORK=artifacts/stylegan3-anime-face-gen.pkl

python gen_images.py \
    --outdir=$OUTDIR \
    --trunc=$TRUNC \
    --seeds=$SEEDS \
    --network=$NETWORK
```

You can play around with the value for seeds to see different results.

Unlike the original StyleGAN3 repo, the generator script makes use of your CPU if CUDA is not available.
It may take time to generate images depending on your CPU spec.

3. The output images will be in the `out` folder.
