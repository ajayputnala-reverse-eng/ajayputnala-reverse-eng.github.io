---
title: Writing Your First OpenCV Bot Script in Python
date: 2026-05-07 10:00:00 +0530
categories: [Tutorials, Automation]
tags: [python, opencv, scripting]
---

## From Theory to Practice

In our last post, we discussed the logic loop of a screen-reading bot: Capture, Analyze, Act, and Sleep. Today, we are turning that logic into a working Python script.

For this example, imagine we are playing a strategy game and want to automate clicking a "Collect" or "Help Guild" button. 

### Step 1: Prepare Your Target Image
Before running the code, you need to take a screenshot of your game and crop out the exact button you want the bot to click. Save this small image as `target_button.png` in the same folder where you will write your Python script.

### Step 2: The Python Script
Create a new file called `bot.py` in your local directory and paste the following code. Make sure you have installed the required libraries (`pip install opencv-python pyautogui numpy`).
```python
import cv2
import numpy as np
import pyautogui
import time

def find_and_click():
    # Give yourself 3 seconds to switch to the game window
    print("Starting scan in 3 seconds...")
    time.sleep(3)

    # 1. Capture the screen
    print("Taking screenshot...")
    screenshot = pyautogui.screenshot()
    # Convert the screenshot to an OpenCV-friendly format
    screenshot = cv2.cvtColor(np.array(screenshot), cv2.COLOR_RGB2BGR)

    # 2. Load the target image we want to find
    template = cv2.imread('target_button.png')
    
    # 3. Analyze the screen for the target
    result = cv2.matchTemplate(screenshot, template, cv2.TM_CCOEFF_NORMED)
    
    # 4. Set a confidence threshold (0.8 = 80% match certainty)
    threshold = 0.8
    locations = np.where(result >= threshold)

    # 5. Act on the results
    if len(locations[0]) > 0:
        # Get the exact X and Y coordinates of the first match
        click_y, click_x = locations[0][0], locations[1][0]
        
        print(f"Target found at X:{click_x}, Y:{click_y}! Clicking now.")
        pyautogui.click(x=click_x, y=click_y)
    else:
        print("Target not found on the screen.")

# Run the function
if __name__ == "__main__":
    find_and_click()
