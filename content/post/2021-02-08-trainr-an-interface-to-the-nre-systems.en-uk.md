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

## Example (Last rendered on 2021-05-02 12:13)

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
## Reading (RDG) Station Board on 2021-05-02 12:13:43
## Time   From                                    Plat  Expected
## 13:06  Bournemouth                             7     On time
## 13:09  Weston-super-Mare                       10    On time
## 13:10  Didcot Parkway                          15A   On time
## 13:12  London Paddington                       9     On time
## 13:15  London Paddington                       8     On time
## 13:15  London Paddington                       12B   On time
## 13:15  London Paddington                       14    13:10
## 13:15  Penzance                                11    13:10
## 13:33  Basingstoke                             2     On time
## 13:38  Gatwick Airport                         5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Bristol Temple Meads                    11    On time
## 13:42  London Paddington                       14    On time
## 13:45  Salisbury                               1     On time
## 13:45  Swansea                                 10    On time
## 13:53  London Paddington                       8     On time
## 13:56  Great Malvern                           10A   On time
## 14:00  London Paddington                       9     On time
## 14:07  Redhill                                 15    On time
## 14:12  Didcot Parkway                          15A   On time
## 14:12  London Paddington                       8     On time
## 14:13  Bristol Temple Meads                    10    On time
## 14:15  London Paddington                       12B   On time
## 14:15  London Paddington                       14    On time
## 14:15  London Paddington                       9     On time
## 14:28  Penzance                                11    On time
## 14:33  Basingstoke                             2     On time
## 14:38  Gatwick Airport                         5     On time
## 14:39  Manchester Piccadilly                   13    On time
## 14:44  London Paddington                       14    On time
## 14:49  Salisbury                               1     On time
## 14:49  Swansea                                 10    On time
## 14:53  London Paddington                       8     On time
## 14:56  Worcester Foregate Street               11A   On time
## 15:00  London Paddington                       9     On time
## 15:07  Redhill                                 6     On time
## 13:15  Virginia Water                          BUS   On time
## 13:17  Newbury                                 BUS   On time
## 13:25  Virginia Water                          BUS   On time
## 13:45  Virginia Water                          BUS   On time
## 13:50  Newbury                                 BUS   On time
## 13:55  Virginia Water                          BUS   On time
## 13:57  Bedwyn                                  BUS   On time
## 14:15  Virginia Water                          BUS   On time
## 14:25  Virginia Water                          BUS   On time
## 14:45  Virginia Water                          BUS   On time
## 14:50  Newbury                                 BUS   On time
## 14:55  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-02 12:13:46
## Time   To                                      Plat  Expected
## 13:12  Ealing Broadway                         15A   On time
## 13:12  Salisbury                               1     On time
## 13:14  Worcester Foregate Street               9     On time
## 13:15  London Paddington                       10    On time
## 13:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 13:17  London Paddington                       11    On time
## 13:17  Plymouth                                8     On time
## 13:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:25  Didcot Parkway                          12B   On time
## 13:30  Ealing Broadway                         14    On time
## 13:38  Basingstoke                             2     On time
## 13:41  Redhill                                 6     On time
## 13:42  London Paddington                       11    On time
## 13:47  London Paddington                       10    On time
## 13:52  Bournemouth                             7     On time
## 13:54  Bristol Temple Meads                    8     On time
## 14:00  Ealing Broadway                         14    On time
## 14:00  London Paddington                       10A   On time
## 14:09  Carmarthen                              9     On time
## 14:12  Salisbury                               1     On time
## 14:13  Ealing Broadway                         15A   On time
## 14:13  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 14:15  Hereford                                8     On time
## 14:15  London Paddington                       10    On time
## 14:17  Penzance                                9     On time
## 14:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:25  Didcot Parkway                          12B   On time
## 14:30  Ealing Broadway                         14    On time
## 14:36  London Paddington                       11    On time
## 14:38  Basingstoke                             2     On time
## 14:41  Redhill                                 15    On time
## 14:54  Bristol Temple Meads                    8     On time
## 14:59  London Paddington                       10    On time
## 15:00  Ealing Broadway                         14    On time
## 15:00  London Paddington                       11A   On time
## 15:09  Swansea                                 9     On time
## 15:12  Salisbury                               1     On time
## 13:26  Virginia Water                          BUS   On time
## 13:35  Bedwyn                                  BUS   On time
## 13:36  Virginia Water                          BUS   On time
## 13:40  Newbury                                 BUS   On time
## 13:56  Virginia Water                          BUS   On time
## 14:06  Virginia Water                          BUS   On time
## 14:26  Virginia Water                          BUS   On time
## 14:35  Newbury                                 BUS   On time
## 14:36  Virginia Water                          BUS   On time
## 14:40  Newbury                                 BUS   On time
## 14:56  Virginia Water                          BUS   On time
## 15:06  Virginia Water                          BUS   On time
```
