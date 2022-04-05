# StyleGAN3 Anime Face Generator

This repository is a subset of the [StyleGAN3 repo by NVIDIA](https://github.com/NVlabs/stylegan3) 
focused on simply generating images from pre-trained model pickle files.

You can use any pre-trained StyleGAN3 model, but for the scope of this repository, 
we will be using a custom pre-trained model on this [Anime Face Dataset](https://github.com/bchao1/Anime-Face-Dataset).

Some generated images:

![seed0006](https://user-images.githubusercontent.com/35907066/161806768-462eab77-0e5f-48b5-950b-2e341a1a95ce.png)
![seed0007](https://user-images.githubusercontent.com/35907066/161806783-89f8fb90-7cf8-4961-b138-98f834be2bd1.png)
![seed0182](https://user-images.githubusercontent.com/35907066/161806795-1500aec4-275c-4ded-83e6-ec06b3eef443.png)
![seed0333](https://user-images.githubusercontent.com/35907066/161806865-3cd78579-4463-46ec-98f2-6537cd52c13b.png)
![seed0987](https://user-images.githubusercontent.com/35907066/161806880-aaa58baa-16d0-482a-8b6c-bddb8408d38c.png)

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
