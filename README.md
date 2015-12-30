Our target for today is to create an application that downloads images from HTML page. And we are expecting pages with a lot of images, and because usually Internet connection is a bottleneck we are going to use multi threading to make parallel downloading of images. So the idea is to download images from the page in multiple threads to speedup that process.

#Let's make it happened

1. Let's take a look at ready to use classes. You have an entry point - Main class. It starts download some content and ask client to provide another URL while it's downloading images for previous URL. Isn't it a cool...
   Also you have another class Page that describes real HTML page. Make sure you understand it's purposes.

2. Let's start with implementing ConnectionUtils class. It contains simple method getData(URL url) and you already have a strong background to implement it.

3. Next, let's take a look at ImageTask class. It is worker class and it's main purposes is to download one image for specified URL. And because it implements Runnable we can use it as a task in executors. Please implement it's main method.

4. Last one is ImageCrawler class. It should process the page and use ExecutorService to download images. We have to use it and execute ImageTasks for each image that we found on the page. Please, make sure to check for the true image URL by using isImageURL method before add it to executor. We should reduce number of tasks on the top level, it's a good practice to do that.

5. That's it. Now you can launch the example and see how images start appear in specified folder. Go and try to reduce number of threads in the pool to 1 and check out the impact.

6. Think, why we can interact with console while application keeps downloading the stuff?