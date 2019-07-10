# boral
tensorflow trained model for detecting forklifts and trucks

## training dataset
pictures of forklifts and trucks downloaded from http://www.image-net.org (need to sign up account and request access to original files).
If you already have sample images of machinery parts from the boral site, use those instead

## training instructions

1. Add images within its respective directories within the dataset/ dir (eg. dataset/truck/truck1.JPEG, dataset/forklift/forklift1.JPEG etc). Suggest having more than 500 for decent accuracy (maybe from different angles and different backgrounds)

1. Train the model using the following command. More details on parameters here if you want to fine tune https://www.tensorflow.org/hub/tutorials/image_retraining 

```shell
python3 train.py --bottleneck_dir=logs/bottlenecks --how_many_training_steps=10000 --model_dir=inception --summaries_dir=logs/training_summaries/basic --output_graph=logs/output_graph.pb --output_labels=logs/output_labels.txt --image_dir=./dataset
``` 

## using the model
the model can be invoked via flask as the API. Start the app with the following

```shell
sudo python3 app.py
```

once the app is running, you can test the API by sending a HTTP request with the 'image' header and base64 of your image as the value. 

![postman_example](https://injae-public-download.s3.amazonaws.com/pictures/postman.png)
