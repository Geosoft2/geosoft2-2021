# Area of Applicability - Practice 
@Hes097

## Allgemeine Informationen: 
* Area of Applicability (AOA) ist ein Bestandteil des R-package Cast 
* Funktion ermittelt den Dissimilarity Index (DI) und leitet basierend auf einen festgelegten Grenzwert die AOA eines Vorhersagemodells ab 
* die AOA wird auf Grundlage von Trainingsdaten und neuen Daten geschätzt
* Trainingsmodell wird mithilfe des caret Package trainiert 
* die trainierten Daten dienen dazu die Relevanz der Variablen zu ermitteln
* daraus lassen sich dann die predictor variables bestimmen
* die Kenntnis über die Area of Applicability ist dann wichtig, wenn Vorhersagen genutzt werden um Entscheidungen zu treffen 

## Funktionalität & Verwendung:  

### Aufbau der Funktion
    aoa( 
      newdata,
      model = NA,
      cl = NULL, 
      train = NULL, 
      weight = NA, 
      variables "all", 
      folds = NULL, 
      returnTrainDI = TRUE
    )

### Argumente der Funktion
    
* newdata 
  * Eingabe eines RasterStack, Rasterbrick oder data frame
  * Daten worüber das Modell Vorhersagen treffen soll 
* model 
  * mit caret erstelltes Trainingsmodell 
  * wird zur Extraktion der Gewichtung verwendet
  * cross-validation folds zur Überprüfung des trainierten Modells
* cl 
  * nimmt ein Cluster-Objekt entgegen 
  * nur notwendig, falls die Eingabedaten (newdata) relativ groß sind 
* train   
  * Funktion zum Training eines data frames
  * enthält die Daten, die für das Training genutzt werden sollen
  * sollte nur genutzt werden, falls kein Trainingsmodell (model) übergeben wird 
* weight 
  * Gewichtung der Variablen
  * nur notwendig, falls kein Trainingsmodell (model) vorhanden ist 
* variables 
  * Eingabe der predictor variables (als Vector) 
  * bei "all" werden alle Variablen des Modells oder trainierten Datensatzes verwendet 
* folds 
  * dient der cross-validation 
  * sollte genutzt werden, falls Replikate verwendet werden 
  * muss genutzt werden, falls kein Trainingsmodell (model) verwendet wird 
* returnTrainDI
  * falls der Dissimilation Index der Traingsdaten als Attribut zurückgegeben werden soll

## Arbeitsprozess zur Bestimmung der Area of Applicability: 

#### 1. Prepare sample data 
* Anzahl der data points müssen bestimmt werden 
* Gewichtung der Variablen 
* Festlegung des Settings der predictors und response 
* Predictors und response werden dann auf der Grundlage einer Prinicipal Component Analysis (PCA) erstellt 
* weitere Aufbereitungsschritte möglich
#### 2. Visualize data spatially 
* Visualisierung der Daten 
#### 3. Train a model 
* Das Training des Modells wird mithilfe des caret Package durchgeführt 
* Caret nutzt die Random Forest Implementierung von Liaw and Wiener (2002) 
* Als Vorbereitung werden dafür die predictor variables extrahiert
* Das Ausgabemodell gibt erste Informationen über die erwartete Modellperformance auf der Grundlage der Random Cross Validation 
#### 4. Calculate the AOA of the trained model for the study area
* Berechnung der AOA kann relativ viel Zeit einnehmen
* Bei ähnlichen Eigenschaften des betrachteten Gebiets zu den Trainingsdaten ist die Distanz zur predictor variable space gering, wodurch der Dissimilarity Index gegen 0 tendiert 
* Besitzen die beiden Datenmodelle unterschiedliche Eigenschaften ergibt sich ein hoher DI
* Grenzwert wird festgelegt
* die Area of Applicability ist der Bereich, in der der DI einen bestimmten Grenzwert nicht überschreitet
* dieser Grenzwert der AOA ergibt sich aus dem oberen Whisker der DI-Werte der Trainingsdaten

## Beispiele: 

### Beispiel 1:
    
    # NOT RUN { 
      library(sf)
      library(raster)
      library(caret)
      library(viridis)
      library(latticeExtra)
      
    # prepare sample data:
      dat <- get(load(system.file("extdata","Cookfarm.RData",package="CAST")))
      dat <- aggregate(dat[,c("VW","Easting","Northing")],by=list(as.character(dat$SOURCEID)),mean)
      pts <- st_as_sf(dat,coords=c("Easting","Northing"))
      pts$ID <- 1:nrow(pts)
      set.seed(100)
      pts <- pts[1:30,]
      studyArea <- stack(system.file("extdata","predictors_2012-03-25.grd",package="CAST"))[[1:8]]
      trainDat <- extract(studyArea,pts,df=TRUE)
      trainDat <- merge(trainDat,pts,by.x="ID",by.y="ID")
      
      # visualize data spatially:
        spplot(scale(studyArea))
        plot(studyArea$DEM)
        plot(pts[,1],add=TRUE,col="black")
        
      # train a model:
        set.seed(100)
        variables <- c("DEM","NDRE.Sd","TWI")
        model <- train(trainDat[,which(names(trainDat)%in%variables)],
        trainDat$VW, method="rf", importance=TRUE, tuneLength=1,
        trControl=trainControl(method="cv",number=5,savePredictions=T))
        print(model) #note that this is a quite poor prediction model
        prediction <- predict(studyArea,model)
        plot(varImp(model,scale=FALSE))
        
      #...then calculate the AOA of the trained model for the study area:
        AOA <- aoa(studyArea,model)
        spplot(AOA$DI, col.regions=viridis(100),main="Dissimilarity Index")
        #plot predictions for the AOA only:
        spplot(prediction, col.regions=viridis(100),main="prediction for the AOA")+
        spplot(AOA$AOA,col.regions=c("grey","transparent"))
            
      ####
      # Calculating the AOA might be time consuming. Consider running it in parallel:
      ####
      library(doParallel)
      library(parallel)
      cl <- makeCluster(4)
      registerDoParallel(cl)
      AOA <- aoa(studyArea,model,cl=cl
      
      ####
      #The AOA can also be calculated without a trained model.
      #All variables are weighted equally in this case:
      ####
      AOA <- aoa(studyArea,train=trainDat,variables=variables)
      spplot(AOA$DI, col.regions=viridis(100),main="Dissimilarity Index")
      spplot(AOA$AOA,main="Area of Applicability")
      # }

### Beispiel 2: 

### Skalierung und Gewichtung der Daten
![Create Sample data, scale and weight them](https://user-images.githubusercontent.com/82754880/137089044-00e23734-376f-484c-8916-6b41de93904d.jpg)

Initiale Situation in der die Beispieldaten aufbereitet werden. Zuerst werden die Daten skaliert (a) und danach die Variablen nach ihrer Relevanz gewichtet (b). 




### Berechnung des Dissimilation Index innerhalb der Trainingsdaten zum Erhalt des Grenzwertes der AOA
![Calculate the DI within the training data to get the threshold for the AOA](https://user-images.githubusercontent.com/82754880/137089885-a5870f1d-ef06-40e4-8279-7f9472c04be4.jpg)

Darstellung der skalierten und gewichteten Trainingsdaten im zweidimensionalen Raum. Zuerst wird der Durschnitt der mittleren Abstände zwischen allen Trainingsdaten berechnet (a). Als nächstes wird dann der DI der Trainingsdaten ermittelt. Danach wird für jeden Punkt  die Distanz zum nächsten Punkt, der nicht im selben cross-validation fold liegt, berechnet (b). Die bestimmte Distanz wird dann durch den Durschnitt der mittleren Abstände geteilt, so dass man den DI eines Punktes erhält. Dieser Vorgang wird für jeden Punkt wiederholt und man erhält so den Grenzwert der Area of Applicability als den oberen Whisker der DI-Werte (Boxplot in b). In (c) wird der Vorgang für einen weiteren Punkt wiederholt. Bei beiden Beispielen ist der DI größer als der Grenzwert, weshalb die Punkte außerhalb der AOA liegen. 





### Ermittlung der AOA für jeden neuen potenziellen Datenpunkt
![Estimate the AOA for each new potential data point](https://user-images.githubusercontent.com/82754880/137093252-a7c2f17f-0ba4-4a78-94a3-0c6a6bb10d25.jpg)

Der berechnete Grenzwert kann dann auf das gesamte zu untersuchende Gebiet angewendet werden, um die AOA für jeden neuen Datenpunkt abzuleiten. Die im rechten Bild dargestellten Bereiche liegen außerhalb der AOA. 


## Begriffserläuterungen:
Cross validation: Technik bei der eine bestimmte Stichprobe eines Datensatzes reserviert und das Modell darauf nicht trainiert wird. Vor der Fertigstellung wird das Modell an dieser Stichprobe getestet. 

Response: "variable of interest", Variable die durch die Vorhersage gemessen wird. Abhängig vom predictor. 

Predictor: Variable, welche die Response beeinflusst. 

Principal Component Analysis (PCA): Verfahren zur Vereinfachung eines großen Datensatzes. Gesamtzahl der Variablen wird reduziert, so dass der Datensatz besser interpretiert werden kann und gleichzeitig keine Informationen verloren gehen. 

## Referenzen:
https://www.rdocumentation.org/packages/CAST/versions/0.5.0/topics/aoa

https://cran.r-project.org/web/packages/CAST/CAST.pdf

Pebesma, E., Meyer, H. (2020) Predicting into unknown space? Estimating the area of applicability of spatial prediction models

Meyer, H. (2020) Mapping the area of applicability - Case Study 

Pebesma, E., Meyer., H. (2021) Method of the 'Area of Apllicability' (AOA) explained in figures

https://royalsocietypublishing.org/doi/10.1098/rsta.2015.0202

https://cran.r-project.org/web/packages/CAST/vignettes/AOA-tutorial.html
