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

## Example (Last rendered on 2021-05-09 16:16)

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
## Reading (RDG) Station Board on 2021-05-09 16:16:22
## Time   From                                    Plat  Expected
## 17:07  Bournemouth                             7     On time
## 17:10  Weston-super-Mare                       -     Cancelled
## 17:11  Didcot Parkway                          10    17:17
## 17:13  Didcot Parkway                          15    On time
## 17:15  London Paddington                       -     Cancelled
## 17:15  Penzance                                -     Cancelled
## 17:15  Slough                                  12    On time
## 17:22  London Paddington                       -     On time
## 17:23  London Paddington                       -     Cancelled
## 17:33  Basingstoke                             2     On time
## 17:35  London Waterloo                         4     On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  Manchester Piccadilly                   7     On time
## 17:40  Bristol Temple Meads                    -     Cancelled
## 17:44  London Paddington                       14    On time
## 17:45  Swansea                                 -     17:47
## 17:56  London Paddington                       -     Cancelled
## 17:56  Worcester Shrub Hill                    11    18:09
## 18:01  London Paddington                       -     Cancelled
## 18:05  London Waterloo                         4     On time
## 18:07  Redhill                                 6     On time
## 18:11  Didcot Parkway                          -     On time
## 18:13  Bristol Temple Meads                    -     Cancelled
## 18:13  Didcot Parkway                          15    On time
## 18:14  London Paddington                       14    On time
## 18:15  Slough                                  12    On time
## 18:21  Plymouth                                -     Cancelled
## 18:22  London Paddington                       -     On time
## 18:22  London Paddington                       -     Cancelled
## 18:25  London Paddington                       -     Cancelled
## 18:29  London Paddington                       -     Cancelled
## 18:33  Basingstoke                             2     On time
## 18:35  London Waterloo                         4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Manchester Piccadilly                   13    On time
## 18:40  Bristol Temple Meads                    -     Cancelled
## 18:44  London Paddington                       14    On time
## 18:44  Swansea                                 11    On time
## 18:53  London Paddington                       -     Cancelled
## 18:56  Worcester Foregate Street               10    On time
## 18:58  London Paddington                       -     Cancelled
## 19:01  London Paddington                       9     On time
## 19:05  London Waterloo                         4     On time
## 19:07  Redhill                                 15    On time
## 19:09  Paignton                                -     Cancelled
## 19:11  Didcot Parkway                          -     On time
## 19:14  Didcot Parkway                          15    On time
## 19:14  London Paddington                       14    On time
## 17:17  Newbury                                 BUS   On time
## 17:50  Newbury                                 BUS   On time
## 17:57  Bedwyn                                  BUS   On time
## 18:50  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-09 16:16:25
## Time   To                                      Plat  Expected
## 17:12  London Paddington                       -     Cancelled
## 17:12  London Paddington                       10    17:18
## 17:14  Slough                                  15    On time
## 17:14  Worcester Foregate Street               8     On time
## 17:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 17:17  Penzance                                -     Cancelled
## 17:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:23  Didcot Parkway                          -     On time
## 17:23  London Paddington                       -     Cancelled
## 17:24  Bristol Temple Meads                    -     Cancelled
## 17:24  London Waterloo                         4     On time
## 17:25  Didcot Parkway                          12    On time
## 17:31  Ealing Broadway                         14    On time
## 17:38  Basingstoke                             2     On time
## 17:41  Redhill                                 6     On time
## 17:42  London Paddington                       -     Cancelled
## 17:46  London Paddington                       -     17:48
## 17:52  Bournemouth                             7     On time
## 17:54  London Waterloo                         4     On time
## 17:57  Weston-super-Mare                       -     Cancelled
## 18:01  Ealing Broadway                         14    On time
## 18:09  Swansea                                 -     Cancelled
## 18:12  London Paddington                       -     On time
## 18:14  Slough                                  15    On time
## 18:14  Worcester Shrub Hill                    8     On time
## 18:15  London Paddington                       -     Cancelled
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:23  Didcot Parkway                          -     On time
## 18:23  Didcot Parkway                          -     Cancelled
## 18:24  London Waterloo                         4     On time
## 18:25  Didcot Parkway                          12    On time
## 18:26  London Paddington                       -     Cancelled
## 18:28  Penzance                                -     Cancelled
## 18:30  Plymouth                                -     Cancelled
##        via Bristol                             
## 18:31  Ealing Broadway                         14    On time
## 18:38  Basingstoke                             2     On time
## 18:41  London Paddington                       -     Cancelled
## 18:41  Redhill                                 6     On time
## 18:46  London Paddington                       11    On time
## 18:52  Ealing Broadway                         14    On time
## 18:54  London Waterloo                         4     On time
## 18:54  Weston-super-Mare                       -     Cancelled
## 19:03  Plymouth                                -     Cancelled
## 19:08  Bristol Parkway                         9     On time
## 19:12  London Paddington                       -     On time
## 19:13  London Paddington                       -     Cancelled
## 19:14  Ealing Broadway                         15    On time
## 19:14  Worcester Shrub Hill                    8     On time
## 17:35  Bedwyn                                  BUS   On time
## 17:40  Newbury                                 BUS   On time
## 18:35  Newbury                                 BUS   On time
## 18:40  Newbury                                 BUS   On time
```
