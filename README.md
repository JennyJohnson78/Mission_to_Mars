# Mission to Mars

## Overview

BeautifulSoup and Splinter can be used on scraping-friendly sites to "scrape" images and data about those images. Scraped data can then be stored in a non-relational database such as Mongo DB. A web application is then be used to display the data, and alter the design of the web app to accommodate images. In this analysis, Mars data will be scraped for users to navigate between images online.

Analysis Steps:
- Scrape Full-Resolution Mars Hemisphere Images and Titles
- Update the Web App with Mars Hemisphere Images and Titles
- Add Bootstrap 3 Components

## Results

Scrape Full-Resolution Mars Hemisphere Images and Titles

- Visit website to view Mars images

```
# Visit the mars nasa news site
url = 'https://redplanetscience.com/'
browser.visit(url)
```

- Use the DevTools to inspect the page for the proper elements to scrape
- Next, create a list to hold the .jpg image URL string and title for each hemisphere image

```
# Create a list to hold the images and titles.
hemisphere_image_urls = []
```
- Write code to retrieve the full-resolution image URL and title for each hemisphere image

```
# Write code to retrieve the image urls and titles for each hemisphere.
for i in range(4):
    #create empty dictionary
    hemispheres = {}
    browser.find_by_css('a.product-item h3')[i].click()
    element = browser.find_link_by_text('Sample').first
    img_url = element['href']
    title = browser.find_by_css("h2.title").text
    hemispheres["img_url"] = img_url
    hemispheres["title"] = title
    hemisphere_image_urls.append(hemispheres)
    browser.back()

```
- Loop through the full-resolution image URL, click the link, find the Sample image anchor tag, and get the href
- Save the full-resolution image URL string as the value for the img_url key that will be stored in the dictionary
- Save the hemisphere image title as the value for the title key that will be stored in the dictionary
- Add the dictionary with the image URL string and the hemisphere image title to the list
- Print the list of dictionary items
```
# Print the list that holds the dictionary of each image url and title.
hemisphere_image_urls
```

## Summary

![image](https://user-images.githubusercontent.com/67409852/145174812-c880db60-4f43-42d1-87c9-8a976c70a85f.png)

![image](https://user-images.githubusercontent.com/67409852/145175714-3cf7725e-e65f-4b10-bc7a-cbdc8814cf2b.png)

![image](https://user-images.githubusercontent.com/67409852/145175542-27f3bbf0-1461-4549-be7c-3d704d9585a1.png)

![image](https://user-images.githubusercontent.com/67409852/145175151-84667909-1be1-4eff-9b8d-fc98296ba7de.png)

![image](https://user-images.githubusercontent.com/67409852/145175333-29549d2e-f007-4b21-a984-cf8db0ce90bf.png)
