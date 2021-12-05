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

## Example (Last rendered on 2021-12-05 22:03)

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
## Reading (RDG) Station Board on 2021-12-05 22:03:37
## Time   From                                    Plat  Expected
## 21:58  London Paddington                       8     22:17
## 21:59  Great Malvern                           10A   21:56
## 22:05  Plymouth                                11    22:08
## 22:07  London Paddington                       8     22:09
## 22:09  Bristol Temple Meads                    10    22:18
## 22:13  London Paddington                       9     On time
## 22:15  London Paddington                       14    On time
## 22:17  London Paddington                       12B   On time
## 22:24  Newbury                                 1     On time
## 22:25  Didcot Parkway                          13A   On time
## 22:27  London Waterloo                         4     On time
## 22:33  Basingstoke                             13    On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:43  London Paddington                       14    22:46
## 22:43  Swansea                                 10    22:51
## 22:45  Gatwick Airport                         15B   On time
## 22:51  Penzance                                11    22:54
## 22:52  Great Malvern                           10A   On time
## 22:56  London Waterloo                         6     On time
## 23:08  Didcot Parkway                          8A    On time
## 23:12  London Paddington                       10    On time
## 23:14  London Paddington                       7B    On time
## 23:16  London Paddington                       9     On time
## 23:17  Bedwyn                                  3     On time
## 23:22  London Waterloo                         5     On time
## 23:31  London Paddington                       9     On time
## 23:34  Plymouth                                11    On time
## 23:35  London Paddington                       10    On time
## 23:41  Gatwick Airport                         7     On time
## 23:46  Newbury                                 1     On time
## 23:52  London Waterloo                         6     On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-05 22:03:41
## Time   To                                      Plat  Expected
## 22:00  Bristol Temple Meads                    8     22:18
## 22:05  London Paddington                       10A   On time
## 22:09  Swansea                                 8     22:10
## 22:12  London Paddington                       11    On time
## 22:13  Worcester Shrub Hill                    9     22:15
## 22:15  London Paddington                       10    22:19
## 22:17  Didcot Parkway                          12B   On time
## 22:21  London Waterloo                         4     On time
## 22:22  Ealing Broadway                         14    On time
## 22:27  Ealing Broadway                         13A   On time
## 22:44  Newbury                                 1     On time
## 22:47  London Paddington                       10    22:54
## 22:51  Ealing Broadway                         14    On time
## 22:54  London Waterloo                         4     On time
## 22:55  London Paddington                       11    On time
## 22:57  London Paddington                       10A   On time
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:18  Bristol Parkway                         9     On time
## 23:18  Ealing Broadway                         8A    On time
## 23:23  Didcot Parkway                          7B    On time
## 23:38  Bristol Temple Meads                    9     On time
## 23:40  London Paddington                       11    On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
