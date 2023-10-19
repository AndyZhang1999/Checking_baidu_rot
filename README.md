# Checking-Baidu-Rot


>Target:

Identify the picture angle, calculate the corresponding sliding distance, and simulate sliding.

>implementation:

  1. Obtain the original image data set: loop through the Baidu search page to enter the Baidu security verification page, capture 1,500 images, and obtain a large number of duplicate images. After screening these pictures, 144 unique pictures were obtained;

![在这里插入图片描述](https://img-blog.csdnimg.cn/5124b0ad94494ba8b54c8dca0b7e6c16.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAVGFuZzU2MTg=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

2. Create a data set: Generate picture models from various angles. Each different picture has 360 photos from different angles. Mark the forward image. Calculate the relative angles of the photos from different angles to the forward image based on the existing picture name sequence. Rename to create the data set;

![在这里插入图片描述](https://img-blog.csdnimg.cn/17cf39e2bd114730b196357bff83c45d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAVGFuZzU2MTg=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)![在这里插入图片描述](https://img-blog.csdnimg.cn/1eba81026b4749368832d211bf0f2d37.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAVGFuZzU2MTg=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)


3. **Generation of Rules:** Establish sliding rules based on the relationship between sliding distance and image rotation angle. Predicting angles according to the sliding distance rule \(o = \text{angle} \times 360 \times b\) is inaccurate. Therefore, we determine the relationship between angle and sliding distance by sliding unit distances on the security verification page.

4. **Model Training:** Utilize neural networks (considering model size, dataset size, and the receptive field of the model) to train on the dataset, directly predicting the required sliding distance. Since the angle of Baidu's security verification doesn't vary as whole numbers and the changes in sliding distance don't correspond one-to-one with angles, predicting sliding distance directly is more accurate and convenient. Also, the categories for sliding distances are fewer than angles, resulting in fewer model parameters. Moreover, because the purpose of the model is to predict sliding distance with sufficient accuracy, allowing for automated program simulations during verification, it should be trained as much as possible on the current dataset. Given all these factors and considering that the real-world verification images differ from the obtained images (even if they are the same images, they can be affected by varying levels of noise interference, like watermarks), there is no division between training and testing datasets.

> **Performance:**
  
Rapid inference, and accurate prediction (can pass basically within three verifications. According to actual operations and videos on platform 'b', humans also find it relatively challenging to pass security verifications manually).

---

Note: "Baidu" is a Chinese multinational technology company specializing in Internet-related services and products and "b 站" often refers to a popular Chinese video-sharing website named "Bilibili."

https://www.douyin.com/video/7070526136115105054?modeFrom=userPost&secUid=MS4wLjABAAAA1Yrnw5gwCNI_5nHTEeJtXCcSkkqajKIfspcXvw6Oxkg

