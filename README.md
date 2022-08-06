Read Me File:
Introduction:
Biological neural networks define human and animal brain function and intellect and generate ultra-large, spatial, organized graphs. 
Their neuronal arrangement is strongly linked to the spatial organization of the brain's microvasculature, which provides oxygen to the neurons and develops a 
comparable spatial graph. We are offering an expandable dataset of whole-brain vasculature graphs based on multiple multi-center imaging procedures in this project.
This new dataset provides the potential for sophisticated graph learning research to be translated into the realm of neuroscience. In addition, the new dataset 
presents difficult graph learning research problems for the machine learning community, such as how to incorporate biological priors into learning algorithms in a 
meaningful and interpretable fashion.

Features:
Whole brain vascular graphs: These are essential for research topics in Biology and Neuroscience, such as neuronal organization, stroke models, and hemodynamics.
Ready-to-use data and a vast data set: We are giving entire brain graphs from various research organizations and will be constantly updating our dataset.
Data-Loaders: We provide numerous functions for easily processing our data for machine learning research, including the community standard OGB and pyG dataloaders.
Benchmarks: We benchmarked a comprehensive collection of state-of-the-art approaches in link prediction and node classification; we supply all codes and full 
instructions.
VesselGraph is an open source, "living" endeavor :We intend to increase our datasets as soon as more brain imaging becomes publically available.

This is the explanation of how we created the dataset. 
1. Using Voreen, generate a raw graph from segmentation.
To generate the node list and edge list from a segmentation volume, use the Voreen Graph Generation Tool.

2. Prepare the Dataset
Navigate to. /source/dataset preprocessing/ and execute process_edge_list.py using the --node list and --edge list options.

3. Run the generate_ogbl_dataset.py file to generate the dataset files.

4. Make Atlas features
Navigate to. /source/feature generation/atlas annotation/. then run generate node atlas labels.py with the —node list and —edge list options.
Go to ./source/pytorch_dataset/ and run link_dataset.py and node_dataset.py to create pytorch-geometric compatible dataset for link-prediction and node-classification task.

5. Convert Graph G to OGB Dataloader
Run python3 generate ogbl dataset.py —dataset synthetic_graph_3 —splitting strategy in./source/ogb dataset/link_prediction/. —train val test random —data root dir data 0.8 0.1 0.1

6. For Line Graph L(G)
Go to ./source/ogb_dataset/node_classification/ and run python3 generate_ogbn_dataset.py --dataset synthetic_graph_3 --train_val_test 0.8 0.1 0.1 --data_root_dir data
1. Training
To create the node go to ./source/baseline_models/link_prediction/OGB_Node2Vec/ and runpython3 node2vec.py --dataset ogbl-synthetic_graph3_spatial_no_edge_attr
2. Testing
Go to ./source/baseline_models/link_prediction/ and select go a MODEL directory to run

We have run the generate_ogbl_dataset.py to generate the dataset files. We will get the synthetic_graph_3 dataset.

We have run the Process_edge_list.py file to generate the node set file. The given dataset will give us the node list output.

Next, we have run the atlas_verification_visulation.py file to generate the projection of nodes in the voreen extracted graph. This will show us the all the nodes in the given dataset.
This file will also generate the brain picture of the nodes and links.
