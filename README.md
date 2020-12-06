# Custom-Data-pipline-in-Tensorflow-for-images
Writing the efficient data loader in tensorflow with making use of [tensorflows data loader API](https://www.tensorflow.org/api_docs/python/tf/data/Dataset) and [tensorflow datasets](https://www.tensorflow.org/datasets) and generalizing it for loading supervised and unsupervised image data.
The file named [Data_pipline.py](Data_pipline.py) consists the class Data_pipeline which can be imported in the other files. The class can be changed according to the users need. The data loader makes use of GPU and other optimizations like prefetch and parallel calls.

# Parameters Description
The class Data_Pipeline has many parameters
* dataset_list : The list of names of datasets which can be downloaded and loaded using the tensorflow datasets.
* dataset : The name of the dataset to be loaded it can load datasets which are added in the dataset_list list.
* dataset_path : The path to the dataset folder it should be in the format dataset_name/classses/images, if the dataset name is given then first preference is given to that.
* image_size : Size of the image(W,H) to be resized only appicable for the dataset_path(can be changed with single line of code).
* image_preprocessing:
  * "0" : No Normalization
  * "1" : Normalization \[0,1\]
  * "2" : Per Pixel Standardization(tf.image.per_image_standardization)
* split : If True then both train and test dataset are loaded for the given dataset parameter, If dataset_path is given then the dataset is split into the train and test based on 
          the split_ratio by preserving the class balance.
* split_ratio : splitting ratio of dataset.
* data_agumentation : If True data augmentation is applied for the dataset according to given data_agumentation_list.
* data_agumentation_list : The list of callable functions which take input as image and return image.
* labels_required_for_output : If True output dataset object will have the (image,label).
* images_required_for_output : If True output dataset object will have the (image,image). If images_required_for_output and labels_required_for_output are True then output
                                dataset object will have the (image,image,label).
* save_data : If True then dataset are saved according to [tensorflow dataset save](https://www.tensorflow.org/api_docs/python/tf/data/experimental/save) in the save_path.
* save_path : Path to save the dataset.
# Libraries required
* tensorflow = 2.3.1 or higher
* tensorflow_datasets
* numpy
* os
* time
* matplotlib

  
