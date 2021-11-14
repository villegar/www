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

## Example (Last rendered on 2021-11-14 16:03)

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
## Reading (RDG) Station Board on 2021-11-14 16:03:31
## Time   From                                    Plat  Expected
## 15:55  Worcester Shrub Hill                    10    On time
## 15:58  Exeter St Davids                        -     Cancelled
## 16:06  London Paddington                       9     On time
## 16:09  Bristol Temple Meads                    11    16:12
## 16:12  London Paddington                       14    On time
## 16:12  London Paddington                       8B    16:15
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15    On time
## 16:20  London Paddington                       9     16:24
## 16:22  London Waterloo                         6     16:24
## 16:23  London Paddington                       12    On time
## 16:26  London Paddington                       7     On time
## 16:33  Basingstoke                             2     On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:43  Swansea                                 10    On time
## 16:44  London Paddington                       14    On time
## 16:50  London Paddington                       9B    On time
## 16:52  London Waterloo                         4     On time
## 16:57  Great Malvern                           10A   On time
## 16:58  Plymouth                                11    On time
## 17:01  London Paddington                       7B    On time
## 17:06  London Paddington                       9     On time
## 17:08  Eastleigh                               12    On time
## 17:09  Weston-super-Mare                       11    On time
## 17:12  London Paddington                       8B    On time
## 17:12  London Paddington                       14    On time
## 17:13  Didcot Parkway                          15    On time
## 17:20  Bedwyn                                  3     On time
## 17:20  London Paddington                       9     On time
## 17:22  London Waterloo                         6     On time
## 17:23  London Paddington                       12    On time
## 17:26  London Paddington                       7     On time
## 17:33  Basingstoke                             2     On time
## 17:38  Exeter St Davids                        11    On time
## 17:39  Manchester Piccadilly                   7     On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:43  Carmarthen                              11    On time
## 17:44  London Paddington                       14    On time
## 17:50  London Paddington                       9     On time
## 17:52  London Waterloo                         4     On time
## 17:54  Plymouth                                11    On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 16:43  Guildford                               BUS   On time
## 17:13  Guildford                               BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
## 17:54  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-14 16:03:35
## Time   To                                      Plat  Expected
## 16:00  London Paddington                       -     Cancelled
## 16:05  London Paddington                       10    On time
## 16:09  Swansea                                 9     On time
## 16:12  London Paddington                       11    16:13
## 16:14  Hereford                                8B    16:16
## 16:15  Ealing Broadway                         15    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:21  London Waterloo                         4     On time
## 16:22  Ealing Broadway                         14    On time
## 16:25  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12    On time
## 16:29  Plymouth                                7     On time
## 16:38  Basingstoke                             2     On time
## 16:44  Newbury                                 3     On time
## 16:46  London Paddington                       10    On time
## 16:51  London Waterloo                         6     On time
## 16:54  Ealing Broadway                         14    On time
## 16:55  Exeter St Davids                        9B    On time
##        via Bristol                             
## 17:00  London Paddington                       11    On time
## 17:03  Plymouth                                7B    On time
## 17:05  London Paddington                       10A   On time
## 17:09  Swansea                                 9     On time
## 17:12  London Paddington                       11    On time
## 17:14  Ealing Broadway                         15    On time
## 17:14  Great Malvern                           8B    On time
## 17:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 17:21  London Waterloo                         4     On time
## 17:22  Ealing Broadway                         14    On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12    On time
## 17:29  Plymouth                                7     On time
## 17:38  Basingstoke                             2     On time
## 17:40  London Paddington                       11    On time
## 17:42  London Paddington                       10    On time
## 17:44  Bedwyn                                  3     On time
## 17:46  London Paddington                       11    On time
## 17:51  Ealing Broadway                         14    On time
## 17:51  London Waterloo                         6     On time
## 17:52  Eastleigh                               7     On time
## 17:55  Weston-super-Mare                       9     On time
## 18:00  London Paddington                       11    On time
## 16:05  Guildford                               BUS   On time
## 16:45  Guildford                               BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 17:30  Guildford                               BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
