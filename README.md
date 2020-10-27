# Canadian-Wind-Turbines

wind_turbine <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-10-27/wind-turbine.csv')

wind_turbine %>%

    group_by(province_territory) %>%
    
    mutate(mean_turbin=mean(turbine_rated_capacity_k_w),n=n()) %>%
    
    ungroup()%>%
    
    ggplot(aes(x=reorder(province_territory,n),y=mean_turbin))+
    
    geom_col(fill="yellow")+
    
    coord_flip()+
    
    labs(x="",y="",title="Mean turbin capacity (KW) by province",
         caption ="Source: Natural Resources Canada" )+
         
    theme(panel.background = element_blank(),axis.ticks=element_blank(),axis.text =element_text(color="yellow",face="bold",size=16),
    
          title=element_text(color="yellow",size=16), plot.background=element_rect(fill="dark red"),
          
          panel.grid = element_blank())
