# <u> Drying Up Lakes Detection </u>


![Images/great_salt_lake_utah.png](./Images/great_salt_lake_utah.png)
Exposed lake bed in the northern part of the Great Salt Lake in Utah (Source : https://www.nytimes.com/2022/06/07/climate/salt-lake-city-climate-disaster.html)


One of the most visible impacts of Climate Change leading to increasing heat waves across the planet, has been the drying of lakes. The website https://www.karmactive.com/climate-change-drying-water-bodies-across-the-world/ lists around ten major water bodies around the world that are disappearing as a result of Climate Change. This article in CNN https://edition.cnn.com/2022/08/20/world/rivers-lakes-drying-up-drought-climate-cmd-intl/index.html shows how six of these water bodies looked from space. 


Amongst these is Lake Mead, which, as per this article in the Guardian https://www.theguardian.com/environment/2022/jul/21/nasa-images-lake-mead-drought, had been reduced to about 27% of its capacity, seeing its images between 2000 and 2022. To sustain the efforts in such initiatives towards fighting Climate Change, the data needs to be extensive, detailed and high quality. The Earth Explorer website https://earthexplorer.usgs.gov/ is ideal, as it is very easily navigatable, and the images are all of high resolution, with a capability to switch off or on specific features. ![earth_explorer.png](./Images/earth_explorer.png)


This exercise to utilize Computer Vision libraries to detect and segment dried up areas around the banks of Lake Mead is undertaken to see it's effectiveness on Satellite high resolution images. For this exercise, the Images were taken from the NASA Landsat website https://landsat.visibleearth.nasa.gov/view.php?id=88099. As per the site, the NASA/USGS Landsat Program provides the longest continuous space-based record of Earth’s land in existence. Landsat data give us information essential for making informed decisions about Earth’s resources and environment.  Utilizing the image of 2000 as a baseline from the Landsat source, portions of dried up lake water is marked in red contours in the 2022 image.  ![side_by_side.png](./Images/side_by_side.png)


The images of 2000 and 2022 are superimposed on each other so that the differences can be easily visible. Detection of areas with similar intensities is done using Computer Vision libraries such as OpenCV, with its findContours algorithm, which can then be segmented. In the present case, in order to do this detection on reasonably distinct boundaries, a smaller region of interest is chosen. Despite that, thanks to the high resolution of the images, the details are very much visible, ideal for OpenCV. ![overlap_and_larger_roi.png](./Images/overlap_and_larger_roi.png) 


The Image Processing includes Binarization, followed by Thresholding, Morphological and Gradient Operations. It's observed that the some areas of drying up are of the highest intensities, whitish in appearance. Some other dried up boundaries and regions are are greyish. Hence, the Contour Detection is performed twice, first, on a clipped Image of only whitish areas (in magenta), and then, next, with greyish intensities (in blue). OpenCV inRange is utilized to segment these greyish areas, since these are in between those with higher whitish and lower brownish appearance. Also, an area filter is applied to exclude those regions away from the bank with similar greyish intensities, that are clearly not in the drying up zone as reflected in the Satellite Images of 2000 - 2022. ![final_detection.png](./Images/final_detection.png)


It can be seen that the actual area of contours detected as drying up areas are far in excess of that we can see from the 2000 to 2022 changes. As mentioned earlier, there are many areas with similar intensities, even, well inside the lake bank, away from the water. This represents a challenge when we use Image Processing to attempt such detection tasks. On the other hand, given the vastness of the earth's regions of lakes and rivers, this approach may be an economical option in terms of resources vis-a-vis using Neural Networks on large datasets. There are a multitude of Climate Change challenges and problems we face, and on the face of it, it does appear that Computer Vision can play a significant role in improving our understanding of the nature and extent of these challenges.
