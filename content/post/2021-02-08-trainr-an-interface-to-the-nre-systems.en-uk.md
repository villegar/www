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

## Example (Last rendered on 2021-10-31 16:03)

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
## Reading (RDG) Station Board on 2021-10-31 16:03:37
## Time   From                                    Plat  Expected
## 15:21  Swansea                                 10    Delayed
## 15:26  London Paddington                       7     16:00
## 15:39  Manchester Piccadilly                   13    16:01
## 15:40  Bristol Temple Meads                    10    16:06
## 15:53  London Paddington                       9     Delayed
## 15:55  Hereford                                10    On time
## 15:58  Exeter St Davids                        11    16:10
## 16:01  London Paddington                       8     16:07
## 16:05  Ascot                                   4     On time
## 16:09  Bristol Temple Meads                    10    16:17
## 16:11  Guildford                               6     On time
## 16:12  London Paddington                       -     Cancelled
## 16:12  Newbury                                 3     16:21
## 16:13  Didcot Parkway                          15A   On time
## 16:13  London Paddington                       14    On time
## 16:17  Swansea                                 11    Delayed
## 16:23  London Paddington                       9     On time
## 16:23  London Paddington                       12B   On time
## 16:26  London Paddington                       7     On time
## 16:35  Ascot                                   4     On time
## 16:38  Redhill                                 5     16:51
## 16:39  Manchester Piccadilly                   13A   17:08
## 16:44  London Paddington                       14    On time
## 16:53  London Paddington                       9     On time
## 16:58  Bournemouth                             13    17:32
## 16:58  Great Malvern                           10A   On time
## 16:58  Penzance                                11    On time
## 16:59  London Paddington                       7B    On time
## 17:01  London Paddington                       8     On time
## 17:05  Ascot                                   4     On time
## 17:10  Weston-super-Mare                       11    On time
## 17:11  Reigate                                 6     Delayed
## 17:12  London Paddington                       9     On time
## 17:13  Didcot Parkway                          15A   On time
## 17:13  London Paddington                       14    On time
## 17:20  Bedwyn                                  3     On time
## 17:21  Swansea                                 10    On time
## 17:23  London Paddington                       9     On time
## 17:23  London Paddington                       12B   On time
## 17:26  London Paddington                       7     On time
## 17:35  Ascot                                   4     On time
## 17:38  Dorking Deepdene                        5     On time
## 17:38  Exeter St Davids                        -     Cancelled
## 17:39  Manchester Piccadilly                   13    On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:44  London Paddington                       14    On time
## 17:53  London Paddington                       9     On time
## 17:54  Plymouth                                11    On time
## 17:56  Hereford                                10    On time
## 16:18  Basingstoke                             BUS   On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 17:00  Winchester                              BUS   On time
## 17:18  Basingstoke                             BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-31 16:03:40
## Time   To                                      Plat  Expected
## 15:25  London Paddington                       10    Delayed
## 15:27  Plymouth                                7     16:03
## 15:45  London Paddington                       10    16:10
## 15:55  Bristol Temple Meads                    9     Delayed
## 16:00  London Paddington                       11    16:11
## 16:02  London Paddington                       10    On time
## 16:09  Swansea                                 8     On time
## 16:14  Hereford                                -     Cancelled
## 16:15  Ealing Broadway                         15A   On time
## 16:15  London Paddington                       10    16:30
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:18  Redhill                                 6     On time
## 16:21  Ascot                                   4     On time
## 16:25  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12B   On time
## 16:25  London Paddington                       11    Delayed
## 16:27  Penzance                                7     On time
## 16:31  Ealing Broadway                         14    On time
## 16:38  Redhill                                 6     On time
## 16:44  Newbury                                 3     On time
## 16:46  Bournemouth                             13A   17:09
## 16:52  Ascot                                   4     On time
## 16:55  Exeter St Davids                        9     On time
##        via Bristol                             
## 17:00  London Paddington                       11    On time
## 17:01  Ealing Broadway                         14    On time
## 17:02  London Paddington                       10A   On time
## 17:02  Plymouth                                7B    On time
## 17:09  Swansea                                 8     On time
## 17:14  Ealing Broadway                         15A   On time
## 17:14  Great Malvern                           9     On time
## 17:15  London Paddington                       11    On time
## 17:15  Manchester Piccadilly                   13    17:33
##        via Coventry & Stoke-on-Trent           
## 17:18  Redhill                                 5     On time
## 17:21  Ascot                                   4     On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12B   On time
## 17:25  London Paddington                       10    On time
## 17:27  Penzance                                7     On time
## 17:31  Ealing Broadway                         14    On time
## 17:40  London Paddington                       -     Cancelled
## 17:41  Redhill                                 6     On time
## 17:44  Bedwyn                                  3     On time
## 17:45  London Paddington                       10    On time
## 17:51  Ascot                                   4     On time
## 17:55  Weston-super-Mare                       9     On time
## 18:00  Ealing Broadway                         14    On time
## 18:00  London Paddington                       11    On time
## 18:02  London Paddington                       10    On time
## 16:38  Basingstoke                             BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 17:38  Basingstoke                             BUS   On time
## 17:52  Winchester                              BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
