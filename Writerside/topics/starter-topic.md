# Documentazione 
 
## Scopo 
 
Questo programma ha lo scopo di estrarre i metadati e i dati EXIF da immagini JPEG in una cartella, salvare anteprime delle immagini, e creare un report Excel con varie informazioni estratte come posizione GPS, data/ora, orientamento, cartella, ecc.  
 
Inoltre permette di esportare i dati con geolocalizzazione in formato vettoriale GeoJSON e Shapefile. 
 
## Funzionalità principali 
 
- Interfaccia grafica Tkinter per selezionare cartelle e file e visualizzare lo stato 
- Elaborazione ricorsiva di tutte le immagini JPEG in una cartella 
- Lettura metadati EXIF con la libreria piexif 
- Estrazione coordinate GPS e conversione in decimali  
- Salvataggio anteprima ridimensionata delle immagini 
- Creazione report Excel con vari campi estratti dai metadati 
- Esportazione dati con geolocalizzazione in GeoJSON e Shapefile 
- Tracciamento file già processati per evitare duplicati 
 
## Spiegazione del codice 
 
### Import librerie 
 
Inizialmente vengono importati i moduli e le librerie Python necessarie per le diverse funzionalità del programma: 
 
- os, openpyxl - per gestione file e creazione Excel 
- tkinter, ttk - per interfaccia grafica  
- piexif - per estrarre metadati EXIF 
- PIL, ImageTk - per manipolazione immagini   
- geopandas, shapely - per creazione GeoJSON e Shapefile 
- altri moduli di utilità come time, json, ecc. 
 
### Funzioni di utilità 
 
Sono definite alcune funzioni di utilità generiche: 
 
-  show_error_in_listbox  e  show_in_listbox : per mostrare messaggi di errore e log nella listbox dell'interfaccia 
-  load_processed_files  e  save_processed_files : caricano e salvano la lista dei file già processati in formato JSON per evitare duplicati 
 
### Interfaccia grafica 
 
La funzione  create_widgets  crea gli elementi base dell'interfaccia Tkinter: 
 
-  tree : Treeview per mostrare la struttura delle directory 
-  image_label : Label per mostrare l'anteprima delle immagini 
-  listbox : Listbox per log e messaggi di errore 
 
Vengono anche definite le funzioni  on_item_double_click  per aprire l'anteprima ingrandita al doppio click su un'immagine, e  populate_tree  per popolare ricorsivamente la struttura ad albero delle directory. 
 
La funzione  main  crea la finestra principale, i menu, la barra di progressione e gli altri elementi dell'interfaccia. 
 
### Elaborazione immagini 
 
Il cuore del programma è la funzione  process_images  che viene chiamata dal pulsante "Start" e processa ricorsivamente tutte le immagini JPEG in una cartella. 
 
Per ogni immagine vengono svolte le seguenti operazioni: 
 
- Lettura metadati EXIF con get_exif_data  
- Estrazione coordinate GPS con  get_coordinates  
- Conversione orientamento fotocamera in direzione cardinale con  degrees_to_direction  
- Salvataggio anteprima ridimensionata dell'immagine  
- Scrittura di una riga nel foglio Excel con vari campi estratti dai metadati 
- Esportazione dati con geolocalizzazione in GeoJSON e Shapefile 
- Tracciamento file processati per evitare duplicati 
 
Vengono gestiti opportunamente errori e condizioni eccezionali. 
 
La funzione aggiorna anche la barra di progressione e le label con il tempo stimato e file rimanenti. 
 
### Esportazione dati 
 
I dati con geolocalizzazione vengono esportati in GeoJSON e Shapefile tramite le funzioni  save_geojson  e  save_shapefile . 
 
Viene creato un GeoDataFrame con la libreria Geopandas e salvato nei formati vettoriali richiesti. 
 
### Conclusioni 
 
Il programma fornisce un flusso completo per estrarre metadati e geolocalizzazione da immagini JPEG e generare un report con questi dati in Excel. L'interfaccia Tkinter permette un utilizzo interattivo e visualizzazione dello stato di avanzamento. 
 
La documentazione del codice spiega in dettaglio il funzionamento e la struttura modulare con chiara separazione di responsabilità. Sono stati applicati buoni principi di programmazione come gestione errori, evitare duplicazione di codice, commenti, ecc. 
 
Il programma può essere esteso aggiungendo nuove funzionalità di elaborazione delle immagini o esportazione dati. La struttura ad oggetti e modulare facilita il mantenimento e l'evoluzione nel tempo.