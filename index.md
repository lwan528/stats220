library(magick)


laugh_cat <- image_read("laugh_cat.jpg") %>%
 image_scale(500) %>%
  image_annotate(text = "YES, I DID IT",
                 color = "#FFFFFF",
                 size = 30,
                 font = 'Comic Sans',
                 gravity = "south")

yes_text <- image_blank(width = 500,
                        height = 500,
                        color = "#000000") %>%
  image_annotate(text = "WHEN YOU THOUGHT 
  YOU FINISHED 
  ALL YOUR LABS",
                 color = "#FFFFFF",
                 size = 50,
                 font = "Impact",
                 gravity = "center")
                               

tired_cat <-image_read("tired_cat.jpg") %>%
  image_scale(500) %>%
  image_annotate(text = "I QUIT",
                 color = "#FFFFFF",
                 size = 28,
                 font = "Comic Sans",
                 gravity = "south")

not_text <- image_blank(width = 500,
                             height = 500,
                             color = "#000000") %>%
  image_annotate(text = "THEN YOU FOUND 
  THERE ARE  
  FIVE MORE",
                 color = "#FFFFFF",
                 size = 50,
                 font = "Impact",
                 gravity = "center")

first_row <- c(laugh_cat, yes_text) %>%
  image_append()

second_row <- c(tired_cat, not_text) %>%
  image_append()



my_meme <- c(first_row, second_row) %>%
  image_append(stack = TRUE)


image_write(my_meme, "my_meme.png")

