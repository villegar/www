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

## Example (Last rendered on 2021-12-12 14:03)

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
## Reading (RDG) Station Board on 2021-12-12 14:03:20
## Time   From                                    Plat  Expected
## 13:45  London Paddington                       8B    14:20
## 13:55  Great Malvern                           -     Cancelled
## 13:58  Swansea                                 11    14:12
## 14:01  London Paddington                       8     On time
## 14:07  London Paddington                       9     14:22
## 14:09  Bristol Temple Meads                    10    14:24
## 14:10  Didcot Parkway                          13    On time
## 14:10  Guildford                               6     14:19
## 14:12  London Paddington                       9     On time
## 14:13  London Paddington                       14    On time
## 14:17  London Paddington                       13    14:40
## 14:19  Newbury                                 1     On time
## 14:24  Penzance                                11    14:26
## 14:29  Oxford                                  10A   On time
## 14:33  Basingstoke                             2     On time
## 14:39  London Paddington                       9     On time
## 14:41  Manchester Piccadilly                   13    On time
## 14:43  London Paddington                       14    On time
## 14:45  London Paddington                       9     On time
## 14:49  Salisbury                               1     On time
## 14:53  London Paddington                       9     On time
## 14:53  Swansea                                 11    On time
## 14:56  Hereford                                -     Cancelled
## 15:01  London Paddington                       8     On time
## 15:07  Bournemouth                             7     On time
## 15:07  London Paddington                       9     On time
## 15:08  Guildford                               6     On time
## 15:09  Weston-super-Mare                       11    On time
## 15:12  London Paddington                       9B    On time
## 15:13  Didcot Parkway                          15    On time
## 15:13  London Paddington                       14    On time
## 15:14  Penzance                                10    15:20
## 15:15  London Paddington                       12    On time
## 15:18  Newbury                                 3     On time
## 15:23  London Paddington                       9     On time
## 15:29  Oxford                                  10    On time
## 15:33  Basingstoke                             2     On time
## 15:39  Manchester Piccadilly                   7     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:43  London Paddington                       9     On time
## 15:43  London Paddington                       14    On time
## 15:47  Salisbury                               1     On time
## 15:53  London Paddington                       9     On time
## 15:53  Swansea                                 11    On time
## 15:57  Hereford                                10    On time
## 14:15  Virginia Water                          BUS   On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 14:26  Virginia Water                          BUS   On time
## 14:45  Virginia Water                          BUS   On time
## 14:56  Virginia Water                          BUS   On time
## 15:15  Virginia Water                          BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
## 15:26  Virginia Water                          BUS   On time
## 15:45  Virginia Water                          BUS   On time
## 15:56  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-12 14:03:22
## Time   To                                      Plat  Expected
## 13:48  Oxford                                  8B    14:21
## 13:58  London Paddington                       11    14:12
## 14:00  London Paddington                       -     Cancelled
## 14:05  Penzance                                8     On time
## 14:09  Carmarthen                              9     14:23
## 14:12  Ealing Broadway                         13    On time
## 14:12  London Paddington                       10    14:25
## 14:12  Salisbury                               1     On time
## 14:14  Hereford                                9     On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 14:22  Ealing Broadway                         14    On time
## 14:25  Didcot Parkway                          13    14:41
## 14:25  London Paddington                       11    14:27
## 14:31  London Paddington                       10A   On time
## 14:38  Basingstoke                             2     On time
## 14:40  Swindon                                 9     On time
## 14:41  Guildford                               6     On time
## 14:44  Newbury                                 1     On time
## 14:48  Oxford                                  9     On time
## 14:52  Ealing Broadway                         14    On time
## 14:54  London Paddington                       11    On time
## 14:54  Taunton                                 9     On time
## 15:01  London Paddington                       -     Cancelled
## 15:05  Plymouth                                8     On time
## 15:09  Swansea                                 9     On time
## 15:11  London Paddington                       11    On time
## 15:12  Salisbury                               1     On time
## 15:14  Ealing Broadway                         15    On time
## 15:14  Great Malvern                           9B    On time
## 15:15  London Paddington                       10    15:21
## 15:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 15:22  Ealing Broadway                         14    On time
## 15:25  Bristol Temple Meads                    9     On time
## 15:25  Didcot Parkway                          12    On time
## 15:31  London Paddington                       10    On time
## 15:38  Basingstoke                             2     On time
## 15:41  Guildford                               6     On time
## 15:44  Newbury                                 3     On time
## 15:46  London Paddington                       10    On time
## 15:48  Oxford                                  9     On time
## 15:52  Bournemouth                             7     On time
## 15:52  Ealing Broadway                         14    On time
## 15:54  London Paddington                       11    On time
## 15:55  Bristol Temple Meads                    9     On time
## 16:02  London Paddington                       10    On time
## 14:05  Virginia Water                          BUS   On time
## 14:25  Virginia Water                          BUS   On time
## 14:35  Virginia Water                          BUS   On time
## 14:55  Virginia Water                          BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 15:05  Virginia Water                          BUS   On time
## 15:25  Virginia Water                          BUS   On time
## 15:35  Virginia Water                          BUS   On time
## 15:55  Virginia Water                          BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
