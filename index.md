

## About the meme I have created


![my_meme](https://user-images.githubusercontent.com/100745241/159157905-02ec5ec7-22f0-47db-8d95-37dc53a64aef.png)

### The motivation of creating it

This is actually the first thing jumped into my head, when i start thinking about what theme should i do to my meme. And this was also discribed my life from last few weeks (well, with hypothesis), but thoese labs actually killing me as it come one and after. It not means i don't like labs, but sometimes is just **TOO MUCH**.


I will survive, right?



### The adaption of this meme

Basically, it takes a long ride to make it become it today. 

When I knew i need to take make a meme, there was list coming into my mind:
1. What text i want to put on my meme?
2. what pictures I want?
3. What do i want it look like in the last?

#### For the text

The first text i used was "WHEN YOU THOUGHT YOU ALREADY FINISHED ALL YOUR LABS", "THEN YOU FOUND OUT THERE ARE FIVE MORE". However, this turns out the words are too much, they would keep out my cats pictures. So i cut them like what they are looking right now. 

#### For the pictures

The solution for solving the question turns out to be quite simple to me, because when i noticed, i'm already browsing the happy cats and tired cats pictures on [Google images](https://www.google.com.hk/imghp?hl=en)

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



## The R code I used to create the meme
```
library(magick)


laugh_cat <- image_read("laugh_cat.jpg") %>%
 image_scale(500) 

yes_text <- image_blank(width = 500,
                        height = 350,) %>%
  image_annotate(text = "THOUGHT FINISHED 
  ALL YOUR LABS",
                 boxcolor = "#000000",
                 color = "#FFFFFF",
                 size = 30,
                 font = 'Comic Sans',
                 gravity = "south")
                               

tired_cat <-image_read("tired_cat.jpg") %>%
  image_scale(500) 

not_text <- image_blank(width = 500,
                             height = 350) %>%
  image_annotate(text = "NO, YOU GOT 5 MORE",
                 boxcolor = "#000000",
                 color = "#FFFFFF",
                 size = 30,
                 font = 'Comic Sans',
                 gravity = "south")

first_row <- c(laugh_cat, yes_text) %>%
  image_mosaic()


second_row <- c(tired_cat, not_text) %>%
  image_mosaic()



my_meme <- c(first_row, second_row) %>%
  image_append(stack = TRUE)


image_write(my_meme, "my_meme.png")


```
