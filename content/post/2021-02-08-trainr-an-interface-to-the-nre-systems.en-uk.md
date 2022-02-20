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

## Example (Last rendered on 2022-02-20 08:03)

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
## Reading (RDG) Station Board on 2022-02-20 08:03:53
## Time   From                                    Plat  Expected
## 07:51  Ealing Broadway                         7     08:10
## 08:02  Staines                                 -     Cancelled
## 08:07  Guildford                               -     Cancelled
## 08:20  London Paddington                       8     On time
## 08:25  London Paddington                       8     On time
## 08:33  Basingstoke                             2     On time
## 08:44  Salisbury                               1     On time
## 08:49  Clapham Junction                        -     Cancelled
## 08:59  London Paddington                       -     Cancelled
## 09:00  Swindon                                 10    On time
## 09:02  Richmond                                4     On time
## 09:03  London Paddington                       14    On time
## 09:07  London Paddington                       7     On time
## 09:10  Didcot Parkway                          15    On time
## 09:16  London Paddington                       -     Cancelled
## 09:23  London Paddington                       7     On time
## 09:24  Oxford                                  11    On time
## 09:26  Newbury                                 -     Cancelled
## 09:29  Bristol Parkway                         -     Cancelled
## 09:33  Basingstoke                             1     On time
## 09:39  Bristol Temple Meads                    11    On time
## 09:39  Guildford                               -     Cancelled
## 09:44  London Paddington                       14    On time
## 09:47  Salisbury                               1     On time
## 09:51  London Waterloo                         4     On time
## 09:58  Didcot Parkway                          15    On time
## 09:59  Worcester Foregate Street               -     Cancelled
## 08:21  Heathrow Central Bus Stn                BUS   On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-20 08:03:55
## Time   To                                      Plat  Expected
## 08:06  Newbury                                 -     Cancelled
## 08:10  London Paddington                       13    On time
## 08:22  Exeter St Davids                        8     On time
## 08:25  London Waterloo                         -     Cancelled
## 08:26  London Paddington                       7     On time
## 08:33  Bristol Temple Meads                    8     On time
## 08:34  Bedwyn                                  14B   On time
## 08:38  Basingstoke                             2     On time
## 08:38  Didcot Parkway                          14A   On time
## 08:45  Guildford                               -     Cancelled
## 08:50  Ealing Broadway                         14    On time
## 08:56  London Waterloo                         -     Cancelled
## 09:00  Swansea                                 -     Cancelled
## 09:01  London Paddington                       10    On time
## 09:09  Worcester Shrub Hill                    7     On time
## 09:12  Salisbury                               1     On time
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 09:18  Didcot Parkway                          12    On time
## 09:18  Exeter St Davids                        -     Cancelled
## 09:25  London Waterloo                         4     On time
## 09:26  London Paddington                       11    On time
## 09:31  Ealing Broadway                         14    On time
## 09:34  Bristol Temple Meads                    7     On time
## 09:35  London Paddington                       -     Cancelled
## 09:38  Basingstoke                             1     On time
## 09:44  Bedwyn                                  12A   On time
## 09:45  Guildford                               6     On time
## 09:45  London Paddington                       11    On time
## 09:52  Southampton Central                     8     On time
## 09:56  London Waterloo                         4     On time
## 10:01  Ealing Broadway                         14    On time
## 10:02  London Paddington                       -     Cancelled
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
