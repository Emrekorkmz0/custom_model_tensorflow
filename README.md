# custom_model_tensorflow
![Ekran görüntüsü 2024-03-22 160530](https://github.com/Emrekorkmz0/custom_model_tensorflow/assets/130879773/8ed5a5f7-33d1-4f16-84e9-b6bb35a20d26)



# STEP 1
install protos file 

# STEP 2 
install anaconda  then create virtual env which is available python=3.9

# STEP 3
install tensorflow models https://github.com/tensorflow/models

# STEP 4 PACKAGE INSTALLATION
cd models/research
# Compile protos.
protoc object_detection/protos/*.proto --python_out=.
# Install TensorFlow Object Detection API.
cp object_detection/packages/tf2/setup.py .
python -m pip install .
# then
python use_protobuf.py <path to directory> <path to protoc file>

# STEP 5 to test installation
python object_detection/builders/model_builder_tf2_test.py

# STEP 6 create tfRecord file 

# STEP 7 START Training 
python model_main_tf2.py --pipeline_config_path=ssd_efficientdet_d0_512x512_coco17_tpu-8.config --model_dir=training --alsologtostderr


![resultoftensorflow](https://github.com/Emrekorkmz0/custom_model_tensorflow/assets/130879773/69ebc984-765c-45ee-a792-4791f50eeee5)


# Export model
python exporter_main_v2.py --trained_checkpoint_dir=training  --pipeline_config_path=ssd_efficientdet_d0_512x512_coco17_tpu-8.config --output_directory inference_graph

