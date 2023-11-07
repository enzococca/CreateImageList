# CreateImageList

# Documentation
 
## Purpose
 
This program aims to extract metadata and EXIF data from JPEG images in a folder, save image previews, and create an Excel report with various extracted information such as GPS location, date/time, orientation, folder, etc.
 
It also allows you to export data with geolocation in GeoJSON and Shapefile vector format.
 
## Main features
 
- Tkinter graphical interface for selecting folders and files and viewing status
- Recursive processing of all JPEG images in a folder
- Reading EXIF metadata with the piexif library
- GPS coordinate extraction and conversion to decimals
- Saving resized preview of images
- Excel report creation with various fields extracted from metadata
- Exporting data with geolocation to GeoJSON and Shapefile
- Tracking already processed files to avoid duplicates 
## Spiegazione del codice 
 
### Import librerie 
 
Initially, the Python modules and libraries needed for the various program features are imported:
 
- os, openpyxl - for file management and Excel creation
- tkinter, ttk - for graphical interface
- piexif - for extracting EXIF metadata
- PIL, ImageTk - for image manipulation
- geopandas, shapely - for GeoJSON and Shapefile creation
- other utility modules such as time, json, etc.
 
### Utility functions
 
Some generic utility functions are defined:
 
- show_error_in_listbox and show_in_listbox : to show error and log messages in the interface listbox
- load_processed_files and save_processed_files : load and save the list of already processed files in JSON format to avoid duplicates
 
### Graphical interface
 
The create_widgets function creates the basic elements of the Tkinter interface:
 
- tree : Treeview to show the directory structure
- image_label : Label to show preview of images
- listbox : Listbox for logs and error messages
 
Also defined are the functions on_item_double_click to open the enlarged preview when an image is double-clicked, and populate_tree to recursively populate the directory tree structure.
 
The main function creates the main window, menus, progress bar, and other interface elements.
 
### Image processing
 
The heart of the program is the process_images function, which is called by the "Start" button and recursively processes all JPEG images in a folder.
 
The following operations are performed for each image:
 
- Reading EXIF metadata with get_exif_data
- Extracting GPS coordinates with get_coordinates
- Converting camera orientation to cardinal direction with degrees_to_direction
- Saving resized preview of the image
- Writing a row to Excel sheet with various fields extracted from metadata
- Exporting data with geolocation to GeoJSON and Shapefile
- Tracking processed files to avoid duplicates
 
Errors and exceptional conditions are handled appropriately.
 
The function also updates the progress bar and labels with estimated time and remaining files.
 
### Data export.
 
Data with geolocation are exported to GeoJSON and Shapefile using the save_geojson and save_shapefile functions .
 
A GeoDataFrame is created with the Geopandas library and saved in the required vector formats.
 
### Conclusions.
 
The program provides a complete flow to extract metadata and geolocation from JPEG images and generate a report with this data in Excel. The Tkinter interface allows interactive use and visualization of progress.
 
The code documentation explains in detail the operation and modular structure with clear separation of responsibilities. Good programming principles such as error handling, avoidance of code duplication, comments, etc. have been applied.
 
The program can be extended by adding new features of image processing or data export. The object-oriented and modular structure facilitates maintenance and evolution over time.
