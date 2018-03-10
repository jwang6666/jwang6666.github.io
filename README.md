# R SHINY TIPS
###### Jiahui Wang
###### 3-8-2018

## Why Shiny?

There are a thousand ways to build a web application, why choose Shiny?

1. Straight from R --- easy to use!
1. Easy to extend your web application with html/css/JavaScript!
1. Amazingly interactive!


How to get start? --- START FROM TODAY!

1. [Video Tutorials from R studio](https://vimeo.com/rstudioinc/review/131218530/212d8a5a7a/#t=0m0s) -- Every you need to know about Shiny as a fresher is here!
1. Want a quick look? [Written Tutorials from R studio](https://shiny.rstudio.com/tutorial/written-tutorial/lesson1/) suits you better!


How does a shiny web application look like? --- GREAT EXAMPLES!

1. [A web application](https://shiny.rstudio.com/gallery/bus-dashboard.html) shows bus lines in Twin Cities
1. [Pilot version](https://gallery.shinyapps.io/TSupplyDemand/) of the Police Supply & Demand simulation tool.
1. [The New Zealand Tourism Dashboard](https://mbienz.shinyapps.io/tourism_dashboard_prod/)


Basic framework of R Shiny:

To use R Shiny, first, you need to install `shiny` Package:
```
install.packages("shiny")
library(shiny)
```
There are two basic sets for Shiny: 

1. put `ui` and `server` in the same R file -- This suits more for small projects

```
ui <- fluidPage(
   titlePanel("YOUR TITLE"),
   sidebarLayout(
      sidebarPanel(
         sliderInput(
            #YOUR INPUT
      )
      ),
          
      mainPanel(
        # YOUR OUTPUT
      )
   )
)
server <- function(input, output) {
   
   output$distPlot <- renderPlot({
     
     ## PRINT THE OUTPUT
     
   })
}

shinyApp(ui = ui, server = server)

```

1. seperate `ui.R` and `server.R` -- If you have a server with contains hundreds of lines, you might consider to seperate them.

```
shinyUI(fluidPage(
  titlePanel("YOUR TITLE"), 
  sidebarLayout(
    sidebarPanel(
       sliderInput(
         ## input
       )
    ),
   
    mainPanel(
       ## output
    )
  )
))

```
```
shinyServer(function(input, output) {
   
  output$"YOUR OUTPUT" <- renderPlot({
  ## code 
    ## plot/print/... output
  
  })
  
})

```

