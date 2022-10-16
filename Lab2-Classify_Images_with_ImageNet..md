# Lab 2: Classify Images with ImagNet

# 1. Prerequisites:
- Lab1 is completed.

# 2. Run container
	
```
$ cd ~/jetson-inference
$ ./docker/run.sh
```	
	
# 3. Navigate to bin folder in the container

```	
$ root@jetons-nano: /jetson-inference #
$ cd build/aarch64/bin/
$ ls
```
![](images/bin_folder.png)
	
# 4. List the images in the images folder

```	
$ ls images
```	
![](images/list_images.png)
	
	
# 5. Use imagenet to classify images

```
$ imagenet.py "images/object_*.jpg" "images/test/object_%i.jpg"
```
By default, it uses GoogleNet.

![](images/classify_images_GoogleNet.png)
	
![](images/classify_images_GoogleNet-2.png)
	
# 6. Use ImageNet to classify videos

## 6.1 Download a video from the web.

Download a test video - jelly fish video from below link: 

```
$ wget https://nvidia.box.com/shared/static/tlswont1jnyu3ix2tbf7utaekpzcx4rc.mkv -O jellyfish.mkv
```

![](images/download_jellyfish_video.png)


## 6.2 Use ImageNet to classify the video

```
$ imagenet.py data/videos/jellyfish.mkv data/videos/test/jellyfish-googlenet.mkv
```

![](images/classify_video.png)


## 6.3 View the classified video

Go to Jetson Nano to view the video classified.

![](images/result_classify_video-1.png)

![](images/result_classify_video-2.png)

![](images/result_classify_video-3.png)




# 7. Use different classification methods to classify images

By default, it uses `GoogleNet` in ImageNet. You can specify which model to load by setting the `--network` flag in the command line.

![](images/imgenet_networks.png)



## 7.1 Download other classification models

```
$ cd jetson-inference/tools
$ ./download-model.sh
```

![](images/download_models.png)

![](images/model_downloader.png)


	
## 7.2 Use ResNet-18 to classify images

```
$ imagenet.py --network=resnet-18 data/images/dog_0.jpg data/images/test/dog_0-output.jpg
```
![](images/classify_with_resnet18.png)


View the classified image using resnet-18.


![](images/resnet18_result.png)


# 8. Use USB webcam to classify live video streams

```
$ imagenet.py --network=resnet-18 /dev/video0
```
![](images/classify_live_video-1.png)

![](images/classify_live_video-2.png)

![](images/classify_live_video-3.png)

`<END of Lab2>`





