
# Helloooooo there

Here is a meme I made using the R package [{magick}](https://cran.r-project.org/web/packages/magick/vignettes/intro.html).


![my_meme](https://user-images.githubusercontent.com/100745241/159204767-6441b1df-b895-47b6-af87-40e29edc39bc.png)
 
 

### About the motivation of creating it

The theme is the first thing that jumped into my head when I started thinking about what topic should I do for my meme. And this was also described my life from last few weeks (well, with exaggerate), but those labs killed me as it came one and after with no breaks. It does not mean I don't like labs, but sometimes it is a bit... **TOO MUCH**.

I think I will survive.


...Right? :)


### About the adaption of this meme

It takes a long ride to make it become it today. 

When I knew I needed to make a meme, there was a list coming into my mind:
1. What text do I want to put on my meme?
2. what pictures do I want?
3. What do I want it to look like in the last?

#### For the text

The first text I used was like *"WHEN YOU THOUGHT YOU ALREADY FINISHED ALL YOUR LABS"*, *"THEN YOU FOUND OUT THERE ARE FIVE MORE"*. However, this turns out the words are too much, and they would keep out my cats' pictures. So I cut them like what they are looking for right now. 

#### For the pictures

The solution for solving the question turns out to be quite simple to me, because when i noticed, I'm already browsing the happy cats and tired cats pictures on [Google images](https://www.google.com.hk/imghp?hl=en)

##### The pictures i used on my meme

![laugh_cat](https://user-images.githubusercontent.com/100745241/159158679-29b5d76f-98b3-4d05-8a69-586445c2673b.jpg)

![tired_cat](https://user-images.githubusercontent.com/100745241/159158681-41fc0e71-53c7-4db7-9555-3be16d7308ac.jpg)


#### For the looks of meme
To make my meme looks like what it like now, i used following functions:
* ```image_read()```
* ```image_annotate()```
* ```image_scale()```
* ```image_blank()```
* ```c()```
* ```image_append()```
* ```image_mosaic()```




## About the R code I used to create the meme
```r
# load the R package {magick}
library(magick)

# read the first cat image
laugh_cat <- image_read("laugh_cat.jpg") %>%
 image_scale(500) 
 
# make a transparent background square that contains text, type colour and other characters by using image_annotate 
yes_text <- image_blank(width = 500,
                        height = 370,) %>%
  image_annotate(text = "THOUGHT FINISHED 
  ALL YOUR LABS",
                 boxcolor = "#000000",
                 color = "#FFFFFF",
                 size = 30,
                 font = 'Comic Sans',
                 gravity = "south")
                               
# read the second cat image
tired_cat <-image_read("tired_cat.jpg") %>%
  image_scale(500) 

# make a transparent background square that contains text, type colour and other characters by using image_annotate 
not_text <- image_blank(width = 500,
                             height = 350) %>%
  image_annotate(text = "NO, YOU GOT 5 MORE",
                 boxcolor = "#000000",
                 color = "#FFFFFF",
                 size = 30,
                 font = 'Comic Sans',
                 gravity = "south")
                 

# join the images and the text squares together by using the image_mosaic function
first_row <- c(laugh_cat, yes_text) %>%
  image_mosaic()

second_row <- c(tired_cat, not_text) %>%
  image_mosaic()


# join the two rows together to make the final meme
my_meme <- c(first_row, second_row) %>%
  image_append(stack = TRUE)

# save meme as an image file 
image_write(my_meme, "my_meme.png")


```
