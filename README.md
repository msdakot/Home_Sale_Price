# Home_Sale_Price
This was created as a part of assignment for MUSA 507 
pal <- colorNumeric(
  palette = c("yellow","#F08F04","#F0433A", "maroon"),
  domain = df_Train1$SP_1000)

leaflet(df_Train1) %>% setView(lng = -71.08, lat = 42.33, zoom = 12) %>% addProviderTiles(providers$CartoDB.DarkMatter)%>%
  addCircles(lng = df_Train1$Longitud_1, lat = df_Train1$Latitude_1, 
             radius = ~(df_Train1$SP_1000), color = pal(df_Train1$SP_1000),
             weight=1, popup =  ~paste(Parcel_No, Neighborhood, sep = ",")) %>%
  addLegend("topright", pal=pal, values=df_Train1$SP_1000,
    title = "Training/Testing Set",
    opacity = 1)
