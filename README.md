## Introduction

This is basic project of computer vision , which do classification of dog vs cat.
I used Inceptionv3 model and traied it for 15 epochs. 
I got following results 

Epoch 15

225/225 [==============================] - 583s 3s/step - loss: 0.0990 - acc: 0.9631 - val_loss: 0.0643 - val_acc: 0.9780

We can improve it more.


## Things to Kow about project :
1. This is Binary classification so we download the dataset , dataset is in zip format

2. Then we extracted the dataset : Directory Structure

                             dataset
                                |
                                v
                            Cat_vs_Dog
                                |
                                |
                                v
                        ---------------
                        |             |
                        |             |
                        v             v
                    training        testing
                        |             |
                        |             | 
                        v             v
                    |-------|     |--------|  
                    v       v     v        v
                   Dog     Cat   Dog      Cat
                 (11250) (11250) (1250)   (1250)
                    |       |     |        |
                    |       |     |        |
                    v       v     v        v
                 images   images images  images

3. Train generator and validation generator that mean we do data agumentation
    (2 classed and 22498 images found)

4. We download .h5 model 
5. Then we load Inception model with it parameter like (input_shape, including_top & weights)
6. We load the weights using .load_weights() 
7 We freezed the layers because we will use the checkpoint till there of its layers
8. we get the layer till we need the model archiricture , in this case we need till (mixed7) name layer, and check the outpt of that it will show (None, 7 , 7, 768)
9. then set the mixed7 layer as last ayer from inception archirecture (last_output = last_layer.output)
10. get the all layer names using this code :
```
    for layer in pre_trained_model.layers:
    print(layer.name)
```

11.set the further layer that is classification layer like flatten, Dense at last uses 
   ``` model = Model(pre_trained_model.input,x) ```

12 compile and fit the model (compulsory save the model.fit in histoy)

13. plot the model performance using
```
acc = history.history['acc']
val_acc = history.history['val_acc']
loss = history.history['loss']
val_loss = history.history['val_loss']
```

14. Now use model.predict method to predict the classification of given image

15 steps to do inference on image:

    first declare variable path =  "/home/avi/InterviewPre/Project1_Cat_dog_prediction/dataset/cats-v-dogs/testing/cats"
    then use image.load_img(path,taeget_size(150,150)
    then conver img to array -> then expand the dim of image using->  x = np.expand_dims(x, axis=0)
    then do vstack 
    then model.predict(dem_image)


## Download Dataset📝  
Before coding we need the dataset for training. 

Dataset of DOG vs CAT Link
https://download.microsoft.com/download/3/E/1/3E1C3F21-ECDB-4869-8368-6DEBA77B919F/kagglecatsanddogs_5340.zip

##  Requirement 🚀  
1.Tensorflow version 2.10.0

2.VS Code


## Steps to run Project  🔥 

Step 1: Clone the repo using command 

```bash
Git clone https://github.com/avi3108/Project1_Cat_dog_prediction.git
```

Step 2:

```bash
Run the cell one by one
```

Step 3:

```bash
Last cell change the image path with your path
```

## Contact
For any suggestion feel free to Contact email: avijadhavak@gmail.com