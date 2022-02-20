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

## Example (Last rendered on 2022-02-20 20:03)

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
## Reading (RDG) Station Board on 2022-02-20 20:03:47
## Time   From                                    Plat  Expected
## 18:58  Exeter St Davids                        11    20:11
## 19:17  London Waterloo                         4     Delayed
## 19:39  Manchester Piccadilly                   7     20:03
## 19:53  London Paddington                       9     20:11
## 19:55  Hereford                                -     Cancelled
## 20:07  London Paddington                       -     Cancelled
## 20:10  Guildford                               5     On time
## 20:12  Bristol Temple Meads                    10    20:47
## 20:12  London Paddington                       -     Cancelled
## 20:13  Didcot Parkway                          13    On time
## 20:13  London Paddington                       14    On time
## 20:17  London Waterloo                         -     Cancelled
## 20:21  Newbury                                 15    20:23
## 20:24  Oxford                                  -     Cancelled
## 20:27  London Paddington                       7     On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   8     20:51
## 20:42  Exeter St Davids                        -     Cancelled
## 20:43  London Paddington                       14    On time
## 20:46  London Paddington                       -     Cancelled
## 20:49  London Waterloo                         -     Cancelled
## 20:49  Swansea                                 -     Cancelled
## 20:53  London Paddington                       9     On time
## 20:58  Exeter St Davids                        11    21:12
## 20:59  Great Malvern                           -     Cancelled
## 21:07  London Paddington                       -     Cancelled
## 21:07  Southampton Central                     8     On time
## 21:10  Guildford                               15    On time
## 21:11  Bristol Temple Meads                    10    On time
## 21:12  London Paddington                       -     Cancelled
## 21:13  Didcot Parkway                          13    On time
## 21:13  London Paddington                       14    On time
## 21:18  London Waterloo                         4     Delayed
## 21:19  Bedwyn                                  1     On time
## 21:29  London Paddington                       7     On time
## 21:33  Basingstoke                             2     On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:43  London Paddington                       14    On time
## 21:48  London Paddington                       -     Cancelled
## 21:48  Swansea                                 -     Cancelled
## 21:49  London Waterloo                         6     On time
## 21:53  London Paddington                       9     On time
## 21:57  Great Malvern                           -     Cancelled
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-20 20:03:50
## Time   To                                      Plat  Expected
## 18:59  London Paddington                       11    20:12
## 19:25  London Waterloo                         4     Delayed
## 19:52  Southampton Central                     7     20:04
## 19:55  Bristol Temple Meads                    9     20:12
## 20:01  London Paddington                       -     Cancelled
## 20:09  Swansea                                 -     Cancelled
## 20:14  Great Malvern                           -     Cancelled
## 20:14  London Paddington                       10    20:48
## 20:15  Guildford                               6     On time
## 20:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 20:25  Didcot Parkway                          13    On time
## 20:25  London Paddington                       -     Cancelled
## 20:25  London Waterloo                         -     Cancelled
## 20:27  Ealing Broadway                         14    On time
## 20:29  Exeter St Davids                        7     On time
## 20:38  Basingstoke                             2     On time
## 20:44  London Paddington                       -     Cancelled
## 20:47  Newbury                                 15B   On time
## 20:49  Oxford                                  -     Cancelled
## 20:50  London Paddington                       -     Cancelled
## 20:52  Southampton Central                     8     On time
## 20:55  Bristol Temple Meads                    9     On time
## 20:56  London Waterloo                         -     Cancelled
## 20:57  Ealing Broadway                         14    On time
## 20:59  London Paddington                       11    21:13
## 21:01  London Paddington                       -     Cancelled
## 21:09  Swansea                                 -     Cancelled
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:14  Didcot Parkway                          12    On time
## 21:14  London Paddington                       10    On time
## 21:15  Guildford                               5     On time
## 21:15  Worcester Shrub Hill                    -     Cancelled
## 21:25  London Waterloo                         -     Cancelled
## 21:30  Ealing Broadway                         14    On time
## 21:31  Exeter St Davids                        7     On time
## 21:38  Basingstoke                             2     On time
## 21:44  Bedwyn                                  1     On time
## 21:49  Oxford                                  -     Cancelled
## 21:50  London Paddington                       -     Cancelled
## 21:52  Southampton Central                     8     On time
## 21:55  Bristol Temple Meads                    9     On time
## 21:56  London Waterloo                         -     Cancelled
## 21:57  Ealing Broadway                         14    On time
## 22:00  London Paddington                       -     Cancelled
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
```
