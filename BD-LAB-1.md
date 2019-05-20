# **BD-LAB-1**

## **TASK-1** - Загрузка EXCEL-файла
**С помощью download.file () загрузите любой excel файл с портала 
http://data.gov.ua 
и 
считайте его.                                                                                                                               
Поскольку - xls, xlsx - бинарные форматы - установите mode = "wb".                                                                         
Выведите первые 6 срок полученного фрейма данных.** 

```
ПРЕДВАРИТЕЛЬНО:
Загрузка и установка пакета - readxl - для импорта Excel-файлов в R
insatll.packages("readxl")
library("readxl")

Загрузка и установка пакета - XML/HTML - для создания и чтения XML/HTML-файлов
install.packages("XML")
library("XML")
```
```
СПОСОБ 1
download.file("https://data.gov.ua/dataset/c445c6ea-f0c3-4167-abb1-5afb4a0e5499/resource/d55eebcf-4660-4919-96b3-4894be5a6cda/download/nuclear_safety_q1_2019.xlsx","f.excel","auto",TRUE,"wb")
tab.data1<-read_xlsx("f.excel")
Вывести первые 6 строк дата-фрейма:
head(tab.data1, n = 6)
```
```
СПОСОБ 2
download.file("C:\Users\USER\R-STATISTICA - DATA\NUCLEAR SAFETY-2018","f.excel","auto",TRUE,"wb")
tab.data1<-read_xlsx("f.excel")
Вывести первые 6 строк дата-фрейма:
tab.data1[1:6,]
```

```
РЕЗУЛЬТАТ:
# A tibble: 6 x 16
year quarter station   irg irg_index `iodine_ radion~ `iodine_ radion~ stable_radionuc~ `stable_ radion~ cs_137_emission `co_60_ emissio~ cs_137_dump co_60_dump volume index_radioacti~ index_dump
2018    1     ЗАЕС       89     0.13       260          0,01             650              0.03             1980            1020                 4330        3670       8.33e5            0.149 0.33      
2018    1     РАЕС      105     0.16       147              0,01             269              7.0000000000000~ 587             165               4800        620        2.22e6            0.78  9.6000000~
2018    1     ЮУАЕС      45     0.1        76               0,01             116              0.02             136             373               390         370        1.46e4            0.136 0.2839999~
2018    1     ХАЕС       31     0.07       26.8             0,01             37.5             0,01             29.4            13.8             380         NA        2.21e4            0.11  0.03      
2018    2     ЗАЕС       84     0.12       262              0,01             640              0.03             453             1003             4627        3432       8.13e5            0.115 0.91      
2018    2     РАЕС      113     0.17       73               0,01             231              0.06             367             281               13704       813       3.62e6            0.92  0.2800000~
```


## **TASK-2** - Загрузка CSV-файла
**С помощью download.file () загрузите файл getdata_data_ss06hid.csv по ссылке
https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv и
загрузите данные в R.                                                                                                                   
Code book, который объясняет значения переменных, находится по ссылке:
https://www.dropbox.com/s/dijv0rlwo4mryv5/PUMSDataDict06.pdf?dl=0                                                                       
Необходимо найти, сколько property имеют value $ 1000000 +**

```
download.file("https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv","f.csv", "auto", TRUE,"wb")
tab.data2<- read.csv("f.csv")
С устранением NA-значений:
sum(tab.data2$VAL == 24, na.rm = TRUE)
```
```
[1] 53
```

## **TASK-3** - Загрузка XML-файла
**Определите xml файл по ссылке
http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml                                                                   
Сколько ресторанов имеют zipcode 21231?**

```
download.file("http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml","f.xml", "auto", TRUE,"wb")
tab.data3<- xmlRoot(xmlTreeParse("f.xml", useInternal = TRUE ))
sum(xpathSApply(tab.data3, "//zipcode", xmlValue) == 21231) 
```
```
[1] 127
```
