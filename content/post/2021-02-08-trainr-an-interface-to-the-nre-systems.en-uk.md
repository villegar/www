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

## Example (Last rendered on 2021-09-26 08:03)

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
## Reading (RDG) Station Board on 2021-09-26 08:03:37
## Time   From                                    Plat  Expected
## 09:05  London Waterloo                         4     09:02
## 09:12  Slough                                  12    On time
## 09:17  Didcot Parkway                          13    On time
## 09:26  Newbury                                 3     On time
## 09:29  Bristol Parkway                         8     09:41
## 09:33  Slough                                  14    On time
## 09:35  London Waterloo                         4     On time
## 09:41  Gatwick Airport                         5     On time
## 09:58  Didcot Parkway                          15    On time
## 10:03  Southampton Central                     7     On time
## 10:04  Slough                                  14    On time
## 10:05  London Waterloo                         4     On time
## 10:11  Redhill                                 5     On time
## 10:14  Bedwyn                                  15    On time
## 10:16  Slough                                  13    On time
## 10:31  Swansea                                 8     On time
## 10:34  Slough                                  14    On time
## 10:35  London Waterloo                         4     On time
## 10:37  Gatwick Airport                         6     On time
## 10:39  Birmingham New Street                   13    On time
## 10:42  Exeter St Davids                        11    On time
## 10:57  Bristol Parkway                         9     On time
## 10:58  Great Malvern                           8     On time
## 09:18  Basingstoke                             BUS   On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
## 10:00  Basingstoke                             BUS   On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 10:48  Basingstoke                             BUS   On time
## 11:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-09-26 08:03:40
## Time   To                                      Plat  Expected
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Didcot Parkway                          12    On time
## 09:18  Gatwick Airport                         15    On time
##        via Guildford                           
## 09:18  Slough                                  13    On time
## 09:21  London Waterloo                         4     On time
## 09:22  Slough                                  14    On time
## 09:30  Bath Spa                                -     Cancelled
## 09:38  Redhill                                 6     On time
## 09:44  Bedwyn                                  3     On time
## 09:52  Slough                                  14    On time
## 09:54  London Waterloo                         4     On time
## 10:03  Carmarthen                              -     On time
## 10:06  Slough                                  15    On time
## 10:12  Hereford                                8     On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:18  Gatwick Airport                         6     On time
##        via Guildford                           
## 10:21  London Waterloo                         4     On time
## 10:22  Slough                                  14    On time
## 10:26  Didcot Parkway                          13    On time
## 10:27  Penzance                                11    On time
## 10:44  Newbury                                 15    On time
## 10:46  Bournemouth                             13    On time
## 10:51  Bath Spa                                8     On time
## 10:51  London Waterloo                         4     On time
## 10:52  Slough                                  14    On time
## 10:58  Redhill                                 5     On time
## 09:08  Basingstoke                             BUS   On time
## 09:52  Winchester                              BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
## 10:38  Basingstoke                             BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
```
