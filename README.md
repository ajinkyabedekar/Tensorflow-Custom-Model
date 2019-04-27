Step 1: cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations

Step 2: Edit label_map.pbtxt

Step 3: cd C:\Users\ajink\Documents\TensorFlow\scripts\preprocessing

Step 4: Edit xml_to_csv.py

Step 5: python xml_to_csv.py -i C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\images\train -o C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\train_labels.csv

Step 6: python xml_to_csv.py -i C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\images\test -o C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\test_labels.csv

Step 7: cd C:\Users\ajink\Documents\TensorFlow\scripts\preprocessing

Step 8: Edit generate_tfrecord.py

Step 9: python generate_tfrecord.py --label=ship --csv_input=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\train_labels.csv --output_path=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\train.record --img_path=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\images\train

Step 10: python generate_tfrecord.py --label=ship --csv_input=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\test_labels.csv --output_path=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\test.record --img_path=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\images\test

Step 11: cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\training

Step 12: Edit ssd_inception_v2_coco.config

Step 13: cd C:\Users\ajink\Documents\Tensorflow\models\research

Step 14: set PYTHONPATH=C:\Users\ajink\Documents\Tensorflow\models

Step 15: set PYTHONPATH=C:\Users\ajink\Documents\Tensorflow\models\research

Step 16: set PYTHONPATH=C:\Users\ajink\Documents\Tensorflow\models\research\slim

Step 17: python setup.py build

Step 18: python setup.py install

Step 19: cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo

Step 20: python train.py --logtostderr --train_dir=training/ --pipeline_config_path=training/ssd_inception_v2_coco.config

Step 21: cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo

Step 22: tensorboard --logdir=training\

Step 23: cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\training

Step 24: Sort all the files inside training_demo/training by descending time and pick the model.ckpt-* file that comes first in the list. Make a note of the file’s name, as it will be passed as an argument when we call the export_inference_graph.py script.

Step 25: cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo

Step 26: python export_inference_graph.py --input_type image_tensor --pipeline_config_path training/ssd_inception_v2_coco.config --trained_checkpoint_prefix training/model.ckpt-* --output_directory trained-inference-graphs/output_inference_graph_v1.pb

Step 27: cd C:\Users\ajink\Documents\Tensorflow\workspace\training_demo

Step 28: Edit tensorflow_object_detection.py

Step 29: activate tensorflow_gpu

Step 30: python tensorflow_object_detection.py