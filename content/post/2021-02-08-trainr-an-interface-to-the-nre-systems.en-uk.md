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

## Example (Last rendered on 2022-10-23 06:11)

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
## Reading (RDG) Station Board on 2022-10-23 06:11:03
## Time   From                                    Plat  Expected
## 07:28  Ealing Broadway                         9     07:31
## 07:41  Gatwick Airport                         5     07:48
## 07:44  Ealing Broadway                         10    On time
## 08:05  Ascot                                   4     On time
## 08:07  Ealing Broadway                         14    On time
## 08:18  London Paddington                       7     On time
## 08:23  Ealing Broadway                         13    On time
## 08:33  Basingstoke                             2     On time
## 08:35  Ascot                                   6     On time
## 08:37  London Paddington                       7     On time
## 08:44  Salisbury                               1     On time
## 08:49  London Paddington                       14    On time
## 08:58  London Paddington                       7     On time
## 09:03  London Paddington                       7     On time
## 09:03  London Paddington                       14    On time
## 09:04  Didcot Parkway                          15    On time
## 09:05  Ascot                                   4     On time
## 07:25  Heathrow Central Bus Stn                BUS   On time
## 07:57  Heathrow Central Bus Stn                BUS   On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-23 06:11:05
## Time   To                                      Plat  Expected
## 07:10  London Paddington                       7A    On time
## 07:39  Redhill                                 8A    On time
## 07:51  Ascot                                   4     On time
## 07:54  London Paddington                       10    On time
## 08:06  Newbury                                 12B   On time
## 08:11  London Paddington                       13    On time
## 08:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 08:21  Ascot                                   4     On time
## 08:22  Penzance                                7     On time
## 08:24  Didcot Parkway                          13    On time
## 08:24  London Paddington                       14    On time
## 08:34  Bedwyn                                  15    On time
## 08:38  Basingstoke                             2     On time
## 08:39  Exeter St Davids                        7     On time
##        via Bristol                             
## 08:40  Redhill                                 15    On time
## 08:51  Ascot                                   6     On time
## 08:56  Ealing Broadway                         14    On time
## 09:00  Swansea                                 7     On time
## 09:06  Ealing Broadway                         15    On time
## 09:10  Great Malvern                           7     On time
## 07:20  Basingstoke                             BUS   On time
## 07:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:00  Heathrow Airport T3 (Bus)               BUS   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
```
