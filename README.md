## Udacity FEND Project 4: Website Optimization

## Summary

This project required improving the performance of loading and rendering an existing portfolio site. The speed of the site was measured using Chrome dev tools to identify performance bottlenecks, and then optimizations were applied to address those bottlenecks.

## Steps to launch:

1. Clone the repo to your local machine
2. Launch a local http server to test. A simple way to do this on a Unix based OS is to open a terminal window, navigate to the directory of the project, and run a python command:
python -m SimpleHTTPServer 8080
3. In the same directory, run the commend: ./ngrok http 8080 to access a secure public URL to the site.
4. Copy the public URL given by nrok from the terminal window and paste it into your browser to view the site.
5. Use Google PageSpeed Insights to check the Google PageSeed score of the homepage
6. Capture a timeline session while scrolling down the page of pizza.html to check the framerate of this page.

## Optimizations of views/js/main.js for pizza.html

1. Modfied the changePizzaSizes function to select randomPizzaContainer elements by class name (rather than querySelectorAll) and add them to a pizzaElements array.
2. Moved the computation of the dx and newwidth variables outside of the for loop as it doesn't seem necesary to recompute them on each pass through that loop.
3. Modified the updatePositions function to select the mover elements by class name.
4. Since there are only 5 unique phases of the moving pizzas, I moved the phase calculation into its own for loop that appends each phase to an array called phaseList, rather than declaring and setting the phase variable each time.
5. The pizza item styles are changed by accessing the relevant element of the phaseList array as it loops through each element in the items array.
6. Changed the number of pizzas generated on page load to 30.

## Optimizations to views/css/style.css

1. Added backface-visibility: hidden; to the .mover class, to move each animated pizza to its own composite layer.

## Resources referenced:

1. Udacity office hours for P4: https://github.com/udacity/fend-office-hours/tree/master/Web%20Optimization/Effective%20Optimizations%20for%2060%20FPS
2. Google PageSpeed Insights rules: https://developers.google.com/speed/docs/insights/rules
3. Udacity forums for P4: https://discussions.udacity.com/c/nd001-2015-05-06/project-4
4. Optimizing Google Web Fonts blog post: www.hongkiat.com/blog/optimize-google-webfonts/
5. MDN docs on getElementsByClassName: https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName