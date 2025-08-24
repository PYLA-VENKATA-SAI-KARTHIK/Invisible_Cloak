# Invisibility Cloak with OpenCV 🧙‍♂️

Ever wanted a real-life Invisibility Cloak like in Harry Potter? This fun Python script uses the magic of computer vision with OpenCV to make that a reality! It detects a specific color in your webcam feed and replaces it with a static background image, effectively making the colored object disappear.

![Demo GIF of the Invisibility Cloak in action]()
*(A GIF like this is highly recommended for your README!)*

--

## Here is how It Works

The magic is actually a clever computer vision trick similar to a "green screen" effect. The process is broken down into three simple steps:

1.   Capturing the Background: First, the script takes a snapshot of the background without you (or the cloak) in it. This static image is our "empty scene."

2.   Detecting the Cloak:  In the live video feed, the script constantly looks for a specific color (the default is a bright blue). It generates a black-and-white "mask" where the white area represents the cloak and the black area is everything else.

3.   The Magic Trick:  The script then combines the images. It takes the part of the live video *without* the cloak (the black area of the mask) and overlays it on top of the "empty scene" background image, but only where the cloak was detected (the white area of the mask).

The result? The background shows through where the cloak is, making it seem invisible!

##  Features

-   Real-time video processing: The invisibility effect is applied live to your webcam feed.
-   Stable Background: Uses median filtering over several frames to capture a clean, noise-free background.
-   Color Customization: Easily change the HSV color values in the code to make your cloak any color you want!
-   Lightweight & Simple: A clear, well-commented script that's easy to understand and modify.

##  Prerequisites

Before you begin, make sure you have the following installed:
-   Python 3.x
-   A webcam connected to your computer

##  Installation & Setup

1.  Clone the repository: 

    git clone https://github.com/PYLA-VENKATA-SAI-KARTHIK/invisibility-cloak.git
    cd invisibility-cloak
    

2.  Install the required libraries: 
    This project depends on `OpenCV` and `NumPy`. You can install them easily using pip.
    ```bash
    pip install opencv-python numpy
    ```
    *(For a more robust setup, you could include a `requirements.txt` file.)*

##  How to Run

Running the script is simple. Follow these steps:

1.  Execute the Python script from your terminal:
    ```bash
    python main.py
    ```

2.  Clear the background! The terminal will prompt you to move out of the camera's view. The script needs a few seconds to capture a clean image of your background.

3.  Use the cloak!  Once the video window appears, step back in front of the camera and hold up an object of the target color (the default is **blue**). Watch it disappear!

4.  Press 'q' on the video window at any time to quit the application.

## Changing the Cloak Color

Don't have a blue cloth? No problem! You can change the color the script detects by editing the `lower_` and `upper_` HSV values in the `main()` function.

For example, to change the cloak color to **green**:

```python
# Find these lines in main()
lower_blue = np.array([90, 50, 50])
upper_blue = np.array([130, 255, 255])

# And change them to a green range
lower_green = np.array([35, 50, 50])
upper_green = np.array([85, 255, 255])

# Don't forget to update the function call!
mask = create_mask(frame, lower_green, upper_green)
```
Tip: Finding the right HSV values can be tricky. You can find many "HSV color picker" tools online to help you define a range for your specific object and lighting.

## Contributing

Feel free to fork this repository, open issues, and submit pull requests. If you have an idea to improve the script (like adding a GUI for color selection!), I'd love to see it.

---

Made with ❤️ and a little bit of Python magic.
