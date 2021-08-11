# Week Four, Day One: Wednesday (7/28/2021)  
*Using the Neural Style Transfer script we developed during class, replace the content and style images with two images of your own selection. Synthesize the two images by applying the following elements from the exercise.* 

- *Define content and style representations*
- *Extracting style and content*
- *Implementing the style transfer algorithm*
- *Apply regularization term on the high frequency components*

*Describe your implementation of neural style transfer to your content and style images. How did the application of the four steps from above produce your resulting work of art?  Comment on what your work means in terms of your development as a data scientist at William & Mary with forethought to the future (please feel free to take as much artistic license as you wish when answering this last question).* 

# Test Image

For a test run, I merged a photograph of a shiba inu dog and a piece of modern artwork, both of which I retrieved from the website Unsplash. In order to begin transferring the style of the art piece onto the photograph, I had to build a model with several activation layers which learned to identify relevant objects within the source images by detecting edges, lines, and textures, interpreted in turn from raw pixels. This model was then able to reproduce the style of the artist who had produced the painting by synthetically replicating distinctive aspects of the artwork in its reconstruction of a different image. To create a more a natural-looking image, or one that would look more organic to the human eye, regularization was applied to the high-frequency components of the product of the model.  

# Content and Style Images
![image](https://user-images.githubusercontent.com/70035366/127523447-e5e0a519-d768-4e84-938d-5e9cab2f37dd.png)

# Neural Style Transfer Result
![image](https://user-images.githubusercontent.com/70035366/127523515-7643be5b-f80d-41a2-9184-aebed58d071a.png)

# Final Result

For my final result, one that I felt represented my experience with the Jump Start Program, I synthesized an image of C-3PO from the *Star Wars* film franchise and a piece of mosaic artwork. C-3PO is a famous robot from cinematic history who in my view represents an ideal of artificial intelligence. His character combines many of the goals of automated intellect, such as natural language processing abilities, adaptability in complex situations, and most importantly, a sense of self-awareness and personality. Taking this character as a symbol of the future of equitable AI and combining it with a distinctively human piece of mosaic artwork - a type of media that inherently focuses on creating aesthetic harmony from contrasting shards of ceramic, glass, and stone - felt like a good way to represent how, to me, advances in technology are ultimately rooted in different ideals of human creativity. 

# Content and Style Images
![image](https://user-images.githubusercontent.com/70035366/129081358-a7357c3f-5d0b-43f2-b7af-7549c8997e50.png)

# Neural Style Transfer Result
![image](https://user-images.githubusercontent.com/70035366/129081395-5515f72d-0033-4ba1-9e08-a603d3787ecc.png)
