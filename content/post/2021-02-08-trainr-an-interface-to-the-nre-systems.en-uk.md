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

## Example (Last rendered on 2022-08-19 12:04)

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
## Reading (RDG) Station Board on 2022-08-19 12:04:50
## Time   From                                    Plat  Expected
## 12:54  Great Malvern                           10A   13:39
## 12:54  London Paddington                       9     13:15
## 13:00  Penzance                                11    13:30
## 13:05  Southampton Central                     8     13:10
## 13:11  London Paddington                       9     On time
## 13:11  London Waterloo                         4     On time
## 13:12  London Paddington                       14    On time
## 13:14  Cardiff Central                         11    13:30
## 13:16  London Paddington                       9     13:18
## 13:24  Newbury                                 -     Cancelled
## 13:31  Didcot Parkway                          13    On time
## 13:33  Redhill                                 5     On time
## 13:39  Bristol Temple Meads                    10    On time
## 13:40  Newbury                                 1     On time
## 13:41  Birmingham New Street                   7     13:43
## 13:41  London Paddington                       9B    On time
## 13:42  London Paddington                       14    On time
## 13:42  London Waterloo                         6     On time
## 13:45  Swansea                                 10    13:49
## 13:55  Basingstoke                             2     On time
## 13:55  Great Malvern                           -     Cancelled
## 13:56  London Paddington                       9     On time
## 14:02  Penzance                                11    14:22
## 14:03  Didcot Parkway                          13    On time
## 14:09  London Paddington                       14    On time
## 14:11  London Paddington                       9     On time
## 14:11  London Waterloo                         4     On time
## 14:16  Cardiff Central                         11    On time
## 14:16  Slough                                  9     On time
## 14:31  Didcot Parkway                          13    On time
## 14:34  Redhill                                 5     On time
## 14:40  Bristol Temple Meads                    10    On time
## 14:40  London Paddington                       14    On time
## 14:40  Newbury                                 1     On time
## 14:41  London Paddington                       9     On time
## 14:41  London Waterloo                         6     On time
## 14:41  Manchester Piccadilly                   7     On time
## 14:45  Swansea                                 10    On time
## 14:49  Basingstoke                             2     On time
## 14:55  London Paddington                       9     On time
## 14:55  Worcester Shrub Hill                    10A   On time
## 14:59  Didcot Parkway                          13    On time
## 13:11  Heathrow Central Bus Stn                BUS   On time
## 13:46  Heathrow Central Bus Stn                BUS   On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 14:56  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-19 12:04:54
## Time   To                                      Plat  Expected
## 12:57  Bristol Temple Meads                    9     13:16
## 12:57  London Paddington                       10A   13:40
## 13:12  London Waterloo                         6     On time
## 13:12  Newbury                                 1     On time
## 13:13  Swansea                                 9     On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:17  London Paddington                       11    13:31
## 13:18  Worcester Foregate Street               9     13:18
## 13:20  Redhill                                 5     On time
## 13:23  Didcot Parkway                          13    On time
## 13:27  Ealing Broadway                         14    On time
## 13:29  Plymouth                                8     13:47
## 13:31  London Paddington                       -     Cancelled
## 13:32  Basingstoke                             2     On time
## 13:41  London Paddington                       10    On time
## 13:42  London Waterloo                         4     On time
## 13:43  Cardiff Central                         9B    On time
## 13:48  London Paddington                       10    13:50
## 13:55  Didcot Parkway                          13    On time
## 13:57  Ealing Broadway                         14    On time
## 13:58  Bristol Temple Meads                    9     On time
## 13:58  London Paddington                       -     Cancelled
## 14:04  London Paddington                       11    14:23
## 14:12  London Waterloo                         6     On time
## 14:12  Newbury                                 1     On time
## 14:13  Swansea                                 9     On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:18  Great Malvern                           9     On time
## 14:19  London Paddington                       11    On time
## 14:20  Redhill                                 5     On time
## 14:25  Didcot Parkway                          13    On time
## 14:27  Ealing Broadway                         14    On time
## 14:29  Penzance                                7     On time
## 14:32  Basingstoke                             2     On time
## 14:42  London Waterloo                         4     On time
## 14:43  Cardiff Central                         9     On time
## 14:43  London Paddington                       10    On time
## 14:48  London Paddington                       10    On time
## 14:52  Southampton Central                     7     On time
## 14:55  Didcot Parkway                          13    On time
## 14:57  Bristol Temple Meads                    9     On time
## 14:57  Ealing Broadway                         14    On time
## 14:57  London Paddington                       10A   On time
## 13:35  Heathrow Central Bus Stn                BUS   On time
## 14:10  Heathrow Central Bus Stn                BUS   On time
## 14:45  Heathrow Central Bus Stn                BUS   On time
```
