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

## Example (Last rendered on 2021-05-09 14:08)

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
## Reading (RDG) Station Board on 2021-05-09 14:08:04
## Time   From                                    Plat  Expected
## 14:59  London Paddington                       -     Cancelled
## 15:10  Bournemouth                             8     15:06
## 15:10  Weston-super-Mare                       -     Cancelled
## 15:11  Didcot Parkway                          10    Delayed
## 15:13  Didcot Parkway                          15    On time
## 15:14  London Paddington                       14    15:07
## 15:15  Slough                                  12    On time
## 15:16  Penzance                                -     Cancelled
## 15:22  London Paddington                       -     On time
## 15:34  Basingstoke                             2     On time
## 15:35  London Waterloo                         4     On time
## 15:38  Gatwick Airport                         5     On time
## 15:39  Manchester Piccadilly                   8     On time
## 15:40  Bristol Temple Meads                    -     Cancelled
## 15:44  London Paddington                       14    On time
## 15:45  Salisbury                               1     On time
## 15:46  Swansea                                 -     Cancelled
## 15:53  London Paddington                       -     Cancelled
## 15:56  Worcester Shrub Hill                    10    On time
## 16:01  London Paddington                       -     Cancelled
## 16:05  London Waterloo                         4     On time
## 16:07  Redhill                                 6     On time
## 16:11  Didcot Parkway                          -     On time
## 16:13  Bristol Temple Meads                    -     Cancelled
## 16:13  Didcot Parkway                          15    On time
## 16:14  London Paddington                       14    On time
## 16:15  London Paddington                       -     Cancelled
## 16:15  Slough                                  12    On time
## 16:16  Plymouth                                -     Cancelled
## 16:22  London Paddington                       -     On time
## 16:23  London Paddington                       -     Cancelled
## 16:33  Basingstoke                             2     On time
## 16:35  London Waterloo                         4     On time
## 16:38  Gatwick Airport                         5     On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:44  London Paddington                       14    On time
## 16:45  Salisbury                               1     On time
## 16:49  Swansea                                 -     Cancelled
## 16:56  London Paddington                       -     Cancelled
## 16:57  Worcester Foregate Street               10    On time
## 17:05  London Waterloo                         4     On time
## 17:07  Redhill                                 6     On time
## 15:17  Newbury                                 BUS   On time
## 15:50  Newbury                                 BUS   On time
## 15:57  Bedwyn                                  BUS   On time
## 16:50  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-09 14:08:07
## Time   To                                      Plat  Expected
## 15:09  Swansea                                 -     Cancelled
## 15:12  London Paddington                       10    Delayed
## 15:12  London Paddington                       -     Cancelled
## 15:12  Salisbury                               1     On time
## 15:14  Slough                                  15    On time
## 15:14  Worcester Foregate Street               13B   On time
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 15:17  Plymouth                                -     15:20
## 15:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:23  Didcot Parkway                          -     On time
## 15:23  London Paddington                       -     Cancelled
## 15:24  London Waterloo                         4     On time
## 15:25  Didcot Parkway                          12    On time
## 15:31  Ealing Broadway                         14    On time
## 15:37  Oxford                                  -     On time
## 15:39  Basingstoke                             2     On time
## 15:41  Redhill                                 6     On time
## 15:42  London Paddington                       -     Cancelled
## 15:47  London Paddington                       -     Cancelled
## 15:52  Bournemouth                             8     On time
## 15:54  London Waterloo                         4     On time
## 15:54  Taunton                                 -     Cancelled
## 16:01  Ealing Broadway                         14    On time
## 16:09  Swansea                                 -     Cancelled
## 16:12  London Paddington                       -     On time
## 16:12  Salisbury                               1     On time
## 16:14  Slough                                  15    On time
## 16:14  Worcester Shrub Hill                    8     On time
## 16:15  London Paddington                       -     Cancelled
## 16:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 16:17  Penzance                                -     Cancelled
## 16:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:23  Didcot Parkway                          -     On time
## 16:24  Bristol Temple Meads                    -     Cancelled
## 16:24  London Waterloo                         4     On time
## 16:25  Didcot Parkway                          12    On time
## 16:25  London Paddington                       -     Cancelled
## 16:31  Ealing Broadway                         14    On time
## 16:38  Basingstoke                             2     On time
## 16:41  Redhill                                 6     On time
## 16:54  London Waterloo                         4     On time
## 16:58  Bristol Temple Meads                    -     Cancelled
## 16:58  London Paddington                       -     Cancelled
## 16:59  Ealing Broadway                         14    On time
## 15:35  Bedwyn                                  BUS   On time
## 15:40  Newbury                                 BUS   On time
## 16:35  Newbury                                 BUS   On time
## 16:40  Newbury                                 BUS   On time
```
