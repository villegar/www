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

## Example (Last rendered on 2023-02-05 20:03)

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
## Reading (RDG) Station Board on 2023-02-05 20:03:20
## Time   From                                    Plat  Expected
## 19:57  Plymouth                                11    On time
## 20:06  Hereford                                10A   On time
## 20:13  Didcot Parkway                          15A   On time
## 20:13  London Paddington                       9B    On time
## 20:18  London Paddington                       7     On time
## 20:19  London Paddington                       12B   On time
## 20:20  Newbury                                 1     On time
## 20:24  Exeter St Davids                        11    On time
## 20:27  London Paddington                       7     On time
## 20:28  London Paddington                       14    On time
## 20:29  Oxford                                  10    On time
## 20:33  Basingstoke                             2     On time
## 20:35  Carmarthen                              11    On time
## 20:38  London Paddington                       7     On time
## 20:39  Manchester Piccadilly                   8     20:41
## 20:43  Plymouth                                10    On time
## 20:47  London Paddington                       9B    On time
## 20:58  London Paddington                       14    On time
## 20:58  Penzance                                11    On time
## 21:06  Bournemouth                             8     On time
## 21:06  Great Malvern                           10A   On time
## 21:12  London Paddington                       12B   On time
## 21:12  London Paddington                       7     On time
## 21:13  Didcot Parkway                          15    On time
## 21:19  Bedwyn                                  1     On time
## 21:23  Bristol Temple Meads                    11A   On time
## 21:26  London Paddington                       7     On time
## 21:28  London Paddington                       14    On time
## 21:32  Basingstoke                             2     On time
## 21:35  Swansea                                 10    On time
## 21:38  London Paddington                       7     On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:41  London Paddington                       9     On time
## 21:58  London Paddington                       14    On time
## 20:03  Bracknell                               BUS   On time
## 20:10  North Camp                              BUS   On time
## 20:19  Bracknell                               BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:27  North Camp                              BUS   On time
## 20:33  Bracknell                               BUS   On time
## 20:49  Bracknell                               BUS   On time
## 20:50  Chippenham                              BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 20:55  Swindon                                 BUS   On time
## 21:03  Bracknell                               BUS   On time
## 21:19  Bracknell                               BUS   On time
## 21:22  North Camp                              BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 21:33  Bracknell                               BUS   On time
## 21:45  Chippenham                              BUS   On time
## 21:49  Bracknell                               BUS   On time
## 21:55  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-05 20:03:23
## Time   To                                      Plat  Expected
## 20:02  London Paddington                       11    On time
## 20:10  London Paddington                       10A   On time
## 20:14  Ealing Broadway                         15A   On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 20:20  Great Malvern                           9B    On time
## 20:22  Swansea                                 7     On time
## 20:23  Ealing Broadway                         14    On time
## 20:25  Didcot Parkway                          12B   On time
## 20:25  London Paddington                       11    On time
## 20:28  Plymouth                                7     On time
## 20:32  London Paddington                       10    On time
## 20:37  Basingstoke                             2     On time
## 20:42  Weston-super-Mare                       7     On time
## 20:45  London Paddington                       11    On time
## 20:46  Newbury                                 1     On time
## 20:48  London Paddington                       10    On time
## 20:52  Bournemouth                             8     On time
## 20:52  Oxford                                  9B    On time
## 20:53  Ealing Broadway                         14    On time
## 21:02  London Paddington                       11    On time
## 21:10  London Paddington                       10A   On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:14  Ealing Broadway                         15    On time
## 21:15  Didcot Parkway                          12B   On time
## 21:20  Worcester Shrub Hill                    7     On time
## 21:24  Ealing Broadway                         14    On time
## 21:25  London Paddington                       11A   On time
## 21:28  Exeter St Davids                        7     On time
## 21:37  Basingstoke                             2     On time
## 21:42  Bristol Temple Meads                    7     On time
## 21:42  London Paddington                       10    On time
## 21:45  Bedwyn                                  1     On time
## 21:46  Oxford                                  9     On time
## 21:52  Southampton Central                     8     On time
## 21:54  Ealing Broadway                         14    On time
## 20:05  Bracknell                               BUS   On time
## 20:21  Bracknell                               BUS   On time
## 20:27  Chippenham                              BUS   On time
## 20:35  Bracknell                               BUS   On time
## 20:40  North Camp                              BUS   On time
## 20:51  Bracknell                               BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:02  Swindon                                 BUS   On time
## 21:05  Bracknell                               BUS   On time
## 21:21  Bracknell                               BUS   On time
## 21:27  Chippenham                              BUS   On time
## 21:35  Bracknell                               BUS   On time
## 21:35  North Camp                              BUS   On time
## 21:50  North Camp                              BUS   On time
## 21:51  Bracknell                               BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
```
