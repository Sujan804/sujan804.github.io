---
layout: single
title: "How to Make a Map Using ArcGIS Pro"
header:
  teaser: "/images/arcgis/map.jpg"
categories: 
  - GIS
tags:
  - ArcGIS Pro
  - Mapping
  - Tutorial
---

Creating a professional map with **ArcGIS Pro** can be an essential skill for GIS professionals and enthusiasts. This tutorial will guide you through the process step-by-step, ensuring your final product is both accurate and visually appealing.

<div style='display: flex; justify-content: center; margin: 20px 0;'>
    <img src='/images/arcgis/map.jpg' style='width: 80%; height: auto;'>
</div>

## Step 1: Prepare Your Data  
Start by adding your data to the project. Ensure you have relevant datasets like counties and wildfire perimeters. These can be imported from a geodatabase or a shapefile.  

1. **Add Feature Classes**: Load `Counties` and `Wildfires` from your geodatabase into the map.
2. **Check Data Alignment**: Verify that the layers align correctly and have the same coordinate system.

## Step 2: Perform the Analysis  
With your data loaded, perform the necessary spatial analysis:  

1. **Dissolve Wildfire Perimeters**:  
   - Tool: `Dissolve`  
   - Input: `Wildfires`  
   - Output: A single polygon representing wildfire-impacted areas.  
   
2. **Intersect Counties and Wildfires**:  
   - Tool: `Intersect`  
   - Input: Dissolved wildfire perimeters and counties.  
   - Output: A feature class detailing wildfire impacts by county.  

3. **Calculate Area in Acres**:  
   - Add a new field for area.  
   - Use the `Calculate Geometry` tool, selecting US Survey Acres.  

4. **Summarize by County**:  
   - Tool: `Summary Statistics`  
   - Input: Intersected data.  
   - Output: Wildfire area totals for each county.

## Step 3: Join and Symbolize  
1. **Join Summary Statistics to Counties**:  
   - Use the county name as the join key.  

2. **Calculate Percentage Burned**:  
   - Add a field and calculate:  
     ```python
     (!Wildfire_Area! / !Total_Area!) * 100
     ```

3. **Symbolize Counties**:  
   - Use a color ramp to visualize the percentage burned.  
   - Classification: Natural Breaks (Jenks), 5 classes.  

## Step 4: Layout and Export  
Create a visually appealing layout:  

1. **Add Map Elements**:  
   - Title, legend, scale bar, north arrow, and basemap.  
   - Include data sources, your name, and the date.  

2. **Finalize Layout**: Adjust map frame settings to fit your A4 layout.  

3. **Export**: Save as a PDF for sharing.  

## Step 5: Share Your Work  
To share your project:  

1. Save your project as a `.mpkx` (Map Package) file.
2. Upload the `.mpkx` file to ArcGIS Online for easy distribution.  

---

This process demonstrates how to harness the power of **ArcGIS Pro** to create meaningful visualizations. Whether for academic, professional, or personal projects, maps created in ArcGIS Pro provide valuable insights.

Explore more on my [GitHub profile](https://github.com/Sujan804) or contact me for collaboration opportunities!
