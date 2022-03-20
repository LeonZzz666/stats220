# My meme
*I made memes using the R package [{magick}](https://cran.r-project.org/web/packages/magick/vignettes/intro.html).*

**This is my meme:**

![](https://s2.loli.net/2022/03/20/g1oqUBeZDNOFbX5.png)
## *The image I used for my meme are two cats:*
* [Smile cat](https://fanfiber.com/blogs/news/polite-cat-meme-went-viral-is-a-cat-can-possibly-smiling)

![](https://cdn.shopify.com/s/files/1/2195/6819/files/Screen_Shot_2020-04-14_at_3.46.02_PM_large.png?v=1586854010)
* [Crying cat](https://knowyourmeme.com/photos/1434447-crying-cat)

![](https://i.kym-cdn.com/photos/images/original/001/434/447/ce8.png)

## My Code

```
library(magick)
smile_cat <- image_read("https://cdn.shopify.com/s/files/1/2195/6819/files/Screen_Shot_2020-04-14_at_3.46.02_PM_large.png?v=1586854010") %>%
  image_scale(500)

crying_cat <- image_read("https://i.kym-cdn.com/photos/images/original/001/434/447/ce8.png") %>%
  image_scale(500)


stats_text <- image_blank(width = 500, 
                          height = 500, 
                          color = "#000000") %>%
  image_annotate(text = "Facing frustration\nalone",
                 color = "#FFFFFF",
                 size = 50,
                 font = "Impact",
                 gravity = "center")

comp_text <- image_blank(width = 500, 
                         height = 500, 
                         color = "#000000") %>%
  image_annotate(text = "When someone\nasks me:\nAre you alright?",
                 color = "#FFFFFF",
                 size = 50,
                 font = "Impact",
                 gravity = "center")


first_row <- c(smile_cat, stats_text) %>%
  image_append()

second_row <- c(crying_cat, comp_text) %>%
  image_append()



c(first_row, second_row) %>%
  image_append(stack = TRUE)

meme <- image_read("http://localhost:24158/session/preview.png?viewer_pane=1&capabilities=1&host=http%3A%2F%2F127.0.0.1%3A24916")
image_write(meme, "xzha485_meme.png")

```
