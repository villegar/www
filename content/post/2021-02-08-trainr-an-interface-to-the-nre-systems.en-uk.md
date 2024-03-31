---
title: 'trainR: An Interface to the National Rail Enquiries Systems'
author: Roberto Villegas-Diaz
date: '2021-02-08'
slug: trainR-an-interface-to-the-nre-systems
tags:
  - uk-railway
  - nre
Categories:
  - Development
  - R
Description: ''
Tags:
  - Development
  - R
---

<img src="https://raw.githubusercontent.com/villegar/trainR/main/inst/images/logo.png" alt="logo" align="right" height=200px/>

The goal of `trainR` is to provide a simple interface to the 
National Rail Enquiries (NRE) systems. There are few data feeds 
available, the simplest of them is Darwin, which provides real-time 
arrival and departure predictions, platform numbers, delay estimates, 
schedule changes and cancellations. Other data feeds provide historical 
data, Historic Service Performance (HSP), and much more. `trainR` 
simplifies the data retrieval, so that the users can focus on their 
analyses. For more details visit 
https://www.nationalrail.co.uk/46391.aspx.

## Installation

You can install the released version of trainR from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("trainR")
```

And the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("villegar/trainR", "dev")
```

## Setup
Before starting to retrieve data from the NRE data feeds, you must obtain an access token. 
Visit the following website for details: http://realtime.nationalrail.co.uk/OpenLDBWSRegistration/

Once you have received your access token, you have to store it in the `.Renviron` file; this can be 
done by executing the following command:


```r
trainR::set_token()
```

This will open a text file, `.Renviron`, add a new line at the end (as follows):

```bash
NRE="<token>"
```

`<token>` should be replaced by the access token obtained from the NRE. Save the changes and restart 
your R session.

You only need to perform this configuration once.

## Example (Last rendered on 2024-03-31 11:06)

Load `trainR` to your working environment:

```r
library(trainR)
```

### Arrivals board at Reading Station (RDG)


```r
rdg_arr <- trainR::GetArrBoardRequest("RDG")
print(rdg_arr)
```

```
## Reading (RDG) Station Board on 2024-03-31 11:06:47.166189
## Time   From                                    Plat  Expected
## 11:39  Manchester Piccadilly                   7     12:36
## 12:00  London Paddington                       9     12:05
## 12:07  London Paddington                       -     Cancelled
## 12:07  London Paddington                       9     12:24
## 12:09  Bristol Temple Meads                    10    On time
## 12:14  Swindon                                 11    12:16
## 12:15  Ealing Broadway                         14    On time
## 12:18  Plymouth                                10    On time
## 12:19  Newbury                                 1     On time
## 12:31  Cheltenham Spa                          11A   12:53
## 12:32  Basingstoke                             2     On time
## 12:32  Virginia Water                          4     On time
## 12:35  Didcot Parkway                          -     Cancelled
## 12:40  Manchester Piccadilly                   7B    12:42
## 12:42  Ealing Broadway                         14    On time
## 12:44  Swansea                                 11    12:48
## 12:47  Salisbury                               2     On time
## 12:48  London Paddington                       13    On time
## 12:54  London Paddington                       9     On time
## 12:57  Ash                                     5     On time
## 12:57  Great Malvern                           10A   On time
## 13:00  London Paddington                       9     On time
## 13:02  London Waterloo                         4     On time
## 13:05  Eastleigh                               7B    On time
## 13:07  London Paddington                       9     On time
## 13:09  Bristol Temple Meads                    10    On time
## 13:12  London Paddington                       14    On time
## 13:12  London Paddington                       8B    On time
## 13:14  Bristol Parkway                         11    On time
## 13:17  Bedwyn                                  1     On time
## 13:17  Penzance                                10    13:39
## 13:32  Basingstoke                             2     On time
## 13:32  Virginia Water                          4     On time
## 13:35  Didcot Parkway                          13    On time
## 13:39  Manchester Piccadilly                   7B    On time
## 13:42  London Paddington                       14    On time
## 13:44  Swansea                                 10    On time
## 13:47  London Paddington                       12    On time
## 13:47  London Paddington                       8B    On time
## 13:47  Salisbury                               2     On time
## 13:54  London Paddington                       9     On time
## 13:57  Ash                                     5     On time
## 14:00  London Paddington                       9     On time
## 14:02  London Waterloo                         4     On time
## 12:15  Heathrow Airport T3 (Bus)               BUS   On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
## 13:15  Heathrow Airport T3 (Bus)               BUS   On time
## 13:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-31 11:06:49.15581
## Time   To                                      Plat  Expected
## 11:52  Eastleigh                               7     12:37
## 12:05  Penzance                                9     12:06
## 12:10  Carmarthen                              9     12:25
## 12:12  London Paddington                       10    On time
## 12:12  Salisbury                               2     On time
## 12:14  Hereford                                8     On time
## 12:15  London Paddington                       11    12:17
## 12:19  London Paddington                       10    On time
## 12:24  Virginia Water                          4     On time
## 12:26  Didcot Parkway                          12    On time
## 12:29  Ealing Broadway                         14    On time
## 12:36  London Paddington                       11A   12:54
## 12:37  Basingstoke                             2     On time
## 12:43  Newbury                                 1     On time
## 12:48  Swindon                                 13    On time
## 12:50  Ash                                     5     On time
## 12:52  Southampton Airport Parkway             7B    On time
## 12:54  London Waterloo                         4     On time
## 12:55  London Paddington                       11    On time
## 12:56  Bristol Temple Meads                    9     On time
## 12:59  Ealing Broadway                         14    On time
## 13:00  Plymouth                                9     On time
##        via Bristol                             
## 13:02  London Paddington                       10A   On time
## 13:10  Swansea                                 9     On time
## 13:12  London Paddington                       10    On time
## 13:12  Yeovil Pen Mill                         2     On time
## 13:14  Hereford                                8B    On time
## 13:14  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 13:15  London Paddington                       11    On time
## 13:19  London Paddington                       10    13:40
## 13:24  Virginia Water                          4     On time
## 13:26  Didcot Parkway                          12B   On time
## 13:29  Ealing Broadway                         14    On time
## 13:37  Basingstoke                             2     On time
## 13:43  Bedwyn                                  1     On time
## 13:48  Swindon                                 12    On time
## 13:50  Ash                                     5     On time
## 13:52  Oxford                                  8B    On time
## 13:52  Southampton Airport Parkway             7B    On time
## 13:54  London Waterloo                         4     On time
## 13:55  London Paddington                       10    On time
## 13:56  Bristol Temple Meads                    9     On time
## 13:59  Ealing Broadway                         14    On time
## 14:00  Penzance                                9     On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
```
