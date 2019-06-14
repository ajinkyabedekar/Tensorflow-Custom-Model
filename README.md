The project was completed to have the source code to customize the Tensorflow model.

The repository contains the complete source code of the project.

Steps to follow:

1. cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations

2. Edit label_map.pbtxt

3. cd C:\Users\ajink\Documents\TensorFlow\scripts\preprocessing

4. Edit xml_to_csv.py

5. python xml_to_csv.py -i C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\images\train -o C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\train_labels.csv

6. python xml_to_csv.py -i C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\images\test -o C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\test_labels.csv

7. cd C:\Users\ajink\Documents\TensorFlow\scripts\preprocessing

8. Edit generate_tfrecord.py

9. python generate_tfrecord.py --label=ship --csv_input=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\train_labels.csv --output_path=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\train.record --img_path=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\images\train

10. python generate_tfrecord.py --label=ship --csv_input=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\test_labels.csv --output_path=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\annotations\test.record --img_path=C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\images\test

11. cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\training

12. Edit ssd_inception_v2_coco.config

13. cd C:\Users\ajink\Documents\Tensorflow\models\research

14. set PYTHONPATH=C:\Users\ajink\Documents\Tensorflow\models

15. set PYTHONPATH=C:\Users\ajink\Documents\Tensorflow\models\research

16. set PYTHONPATH=C:\Users\ajink\Documents\Tensorflow\models\research\slim

17. python setup.py build

18. python setup.py install

19. cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo

20. python train.py --logtostderr --train_dir=training/ --pipeline_config_path=training/ssd_inception_v2_coco.config

21. cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo

22. tensorboard --logdir=training\

23. cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo\training

24. Sort all the files inside training_demo/training by descending time and pick the model.ckpt-* file that comes first in the list. Make a note of the file’s name, as it will be passed as an argument when we call the export_inference_graph.py script.

25. cd C:\Users\ajink\Documents\TensorFlow\workspace\training_demo

26. python export_inference_graph.py --input_type image_tensor --pipeline_config_path training/ssd_inception_v2_coco.config --trained_checkpoint_prefix training/model.ckpt-* --output_directory trained-inference-graphs/output_inference_graph_v1.pb

27. cd C:\Users\ajink\Documents\Tensorflow\workspace\training_demo

28. Edit tensorflow_object_detection.py

29. activate tensorflow_gpu

30. python tensorflow_object_detection.py