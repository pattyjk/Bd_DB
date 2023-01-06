```
###elements for navigation
# Upper Left Corner NAME
# (1) Submit your microbial data
# (2) Analyze data
# (3) R package
# (4) Tutorials
# (5) GitHub
# (6) Help



ui <- fluidPage(
  theme = shinytheme("sandstone"),
  navbarPage(
    ##########
    ## Main page
    ##########
    "Hippity hoppy database",
   tabsetPanel(
     tabPanel("Home"), 
     tabPanel("Submit your isolates"),
     tabPanel("Analyze data"),
     tabPanel("R Tutorials"),
     tabPanel("GitHub"),
     tabPanel("Help")
     
     ),
    mainPanel(
          h4(" Database last updated 1/5/22 by a frog...ribbit"),
          a(
            href="https://esajournals.onlinelibrary.wiley.com/doi/abs/10.1890/14-1837.1", 
            "Click here to read our publication"
          ),
          h5("This project is funded by the Smithsonian or whoever pays Molly and I."),
          h5("This website allows you to:"),
          tags$li("Submit your isolate data to add to the database"),
          tags$li("Analyze your 16S rRNA gene sequences"),
          tags$li("Learn about and install our R package"),
          tags$li("Learn to use our R package through guided tutorials"),
          tags$li("Access the database's GitHub repo"),
          tags$li("Get help from frog experts for all your frog needs"),
          h5("Please direct any questions, comments, or concerns to someone"),
          a(href="https://photos.app.goo.gl/6q4bHUTgin2CMq5eA", "Click here for a picture of Pat's doggies")
        )
      )
    )
server<- function(input, output) { }
```

## Launch
```
shinyApp(ui, server)
```
