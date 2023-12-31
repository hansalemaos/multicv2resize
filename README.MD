# Parallelized image resizing function using OpenCV and multiprocessing

## pip install multicv2resize

### Tested against Python 3.11 / Windows 10

```python

Parallelized image resizing function using OpenCV and multiprocessing.

This function utilizes the `multiprocnomain` library for parallelizing the resizing process of a batch of images.
The resizing parameters for each image in the batch are specified in a list of dictionaries,
allowing for flexibility in resizing options.

Parameters:
	- pics (list): A list of dictionaries, each containing the following keys:
		- 'img' (Any): Accepts almost any image format
		- 'width' (int, optional): The target width of the resized image. If None, the original width is maintained. - IMPORTANT: (pass either width, height, width and height, or percentage)
		- 'height' (int, optional): The target height of the resized image. If None, the original height is maintained. - IMPORTANT: (pass either width, height, width and height, or percentage)
		- 'percent' (int, optional): The percentage by which to scale the image.  - IMPORTANT: (pass either width, height, width and height, or percentage)
		- 'interpolation' (int, optional): The interpolation method to use during resizing.
		  Defaults to cv2.INTER_AREA.

	- processes (int, optional): The number of parallel processes to use for resizing. Defaults to 5.

	- chunks (int, optional): The number of chunks to divide the resizing tasks into for better load balancing. Defaults to 1.

	- print_stderr (bool, optional): If True, prints stderr messages during the resizing process. Defaults to True.

	- print_stdout (bool, optional): If True, prints stdout messages during the resizing process. Defaults to False.

Returns:
	- dict: A dictionary containing resized images corresponding to the input batch. The keys are generated based on the input image paths.

Example:

	pics0 = [{'img':r"C:\Users\hansc\Pictures\cgea.png",'width':None,'height':None,'percent':percentage,'interpolation':cv2.INTER_AREA} for percentage in range(50,150,1)]
	pics1 = [{'img':r"C:\Users\hansc\Pictures\cgea.png",'width':100+addwidth,'height':100,'percent':None,'interpolation':cv2.INTER_AREA} for addwidth in range(50,150,1)]
	pics=pics0+pics1

	pic=resize_image(pics,processes=5,chunks=1,print_stderr=True, print_stdout=False)
	for k, v in pic.items():
		cv2.imwrite(rf'C:\resi\{k}.png', v)
```