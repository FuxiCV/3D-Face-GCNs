# Towards High-Fidelity 3D Face Reconstruction from In-the-Wild Images Using Graph Convolutional Networks

CVPR 2020, [[pdf]](https://arxiv.org/pdf/2003.05653.pdf) [[arxiv]](https://arxiv.org/abs/2003.05653)

by Jiangke Lin, Yi Yuan*, Tianjia Shao, Kun Zhou

In this paper, we seek to reconstruct the 3D facial shape with high fidelity texture from a single image, without the need to capture a large-scale face texture database.

![An overview of our method.](https://github.com/yiyuan1991/3D-Face-GCNs/blob/master/imgs/overall.jpg)

Here is the official implementation.

#### 1. Requirements
> tensorflow  
> tqdm  
> scikit-learn  
> scipy  
> mesh-renderer

The shapes and coarse textures are from https://github.com/microsoft/Deep3DFaceReconstruction, the GCNs code is based on https://github.com/anuragranj/coma and mesh processing libraries from https://github.com/MPI-IS/mesh.  
Please refer to their project pages for the necessary files.

#### 2. Prepare dataset
As we mentioned in the paper, we use a face segmentation network to segment out the non-face areas. Here, we treat the segmentation result as alpha channel and store it in a `.png` file along with the face image.  
For efficiency, we write all `.png` images into a binary file in advance. Please change the data folder in `create_bin.py` to yours.
> python create_bin.py


#### 3. Training
It is worth mentioning that, our network involves the mesh sampling algorithm. We save the sampling-related parameters into `.npz` files in advance and load them before training to avoid meaningless repeat calculation.  
More details could be found in utils.py#L266 init_sampling().

After the dataset files are ready, the training can be started.
> python main.py --mode train

#### 4. Future Works
As we continue to work on 3D face reconstruction and try to integrate such an algorithm into automatic game character creation, we can expect more results in the future.  
We will also make some of our datasets for 3D face reconstruction public available in the future.  
However, at present, you can try out our current automatic character creation method in the game Justice(逆水寒, https://n.163.com).

#### Citation
    @inproceedings{lin2020towards,  
      title={Towards high-fidelity 3D face reconstruction from in-the-wild images using graph convolutional networks},  
      author={Lin, Jiangke and Yuan, Yi and Shao, Tianjia and Zhou, Kun},  
      booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},  
      pages={5891--5900},  
      year={2020}  
    }