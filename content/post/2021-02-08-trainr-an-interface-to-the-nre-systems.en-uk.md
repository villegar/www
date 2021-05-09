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

## Example (Last rendered on 2021-05-09 10:09)

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
## Reading (RDG) Station Board on 2021-05-09 10:09:01
## Time   From                                    Plat  Expected
## 11:01  London Paddington                       -     Cancelled
## 11:02  Exeter St Davids                        -     Cancelled
## 11:07  Redhill                                 6     11:20
## 11:10  Bournemouth                             8     11:12
## 11:10  Didcot Parkway                          15    On time
## 11:11  Didcot Parkway                          10    On time
## 11:14  London Paddington                       14    On time
## 11:15  Slough                                  12    On time
## 11:17  Bristol Parkway                         -     Cancelled
## 11:17  London Paddington                       -     Cancelled
## 11:22  London Paddington                       9     On time
## 11:33  Basingstoke                             2     On time
## 11:35  London Waterloo                         4     On time
## 11:38  Gatwick Airport                         5     On time
## 11:39  Manchester Piccadilly                   8     On time
## 11:44  London Paddington                       14    On time
## 11:45  Salisbury                               1     On time
## 11:45  Swansea                                 11    On time
## 11:53  London Paddington                       -     Cancelled
## 11:56  Great Malvern                           -     Cancelled
## 11:59  London Paddington                       9     On time
## 12:06  London Waterloo                         4     On time
## 12:07  Redhill                                 6     On time
## 12:10  Didcot Parkway                          15    On time
## 12:11  Bristol Temple Meads                    -     Cancelled
## 12:11  Didcot Parkway                          -     On time
## 12:14  London Paddington                       14    On time
## 12:15  Slough                                  12    On time
## 12:17  London Paddington                       -     Cancelled
## 12:19  Plymouth                                -     Cancelled
## 12:22  London Paddington                       -     On time
## 12:33  Basingstoke                             2     On time
## 12:35  London Waterloo                         4     On time
## 12:38  Gatwick Airport                         5     On time
## 12:39  Manchester Piccadilly                   13    On time
## 12:44  London Paddington                       14    On time
## 12:45  Salisbury                               1     On time
## 12:45  Swansea                                 -     Cancelled
## 12:53  London Paddington                       -     Cancelled
## 12:56  Oxford                                  10    On time
## 13:06  London Waterloo                         4     On time
## 13:07  Redhill                                 6     On time
## 11:57  Bedwyn                                  BUS   On time
## 12:50  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-09 10:09:04
## Time   To                                      Plat  Expected
## 11:09  Swansea                                 -     Cancelled
## 11:10  London Paddington                       -     Cancelled
## 11:12  London Paddington                       10    On time
## 11:12  Salisbury                               1     On time
## 11:12  Slough                                  15    On time
## 11:14  Worcester Foregate Street               13    On time
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:17  Plymouth                                -     Cancelled
## 11:19  London Paddington                       -     Cancelled
## 11:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:23  Didcot Parkway                          9     On time
## 11:24  London Waterloo                         4     On time
## 11:27  Didcot Parkway                          12    On time
## 11:31  Ealing Broadway                         14    On time
## 11:38  Basingstoke                             2     On time
## 11:41  Redhill                                 6     On time
## 11:48  London Paddington                       11    On time
## 11:52  Bournemouth                             8     On time
## 11:54  London Waterloo                         4     On time
## 11:54  Paignton                                -     Cancelled
##        via Bristol                             
## 12:01  Ealing Broadway                         14    On time
## 12:09  Swansea                                 9     On time
## 12:12  London Paddington                       -     On time
## 12:12  Salisbury                               1     On time
## 12:12  Slough                                  15    On time
## 12:13  London Paddington                       -     Cancelled
## 12:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 12:17  Penzance                                -     Cancelled
## 12:18  Worcester Shrub Hill                    8     On time
## 12:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:23  Didcot Parkway                          -     On time
## 12:24  London Waterloo                         4     On time
## 12:27  Didcot Parkway                          12    On time
## 12:28  London Paddington                       -     Cancelled
## 12:31  Ealing Broadway                         14    On time
## 12:38  Basingstoke                             2     On time
## 12:41  Redhill                                 6     On time
## 12:47  London Paddington                       -     Cancelled
## 12:54  London Waterloo                         4     On time
## 12:54  Weston-super-Mare                       -     Cancelled
## 13:00  London Paddington                       10    On time
## 13:01  Ealing Broadway                         14    On time
## 11:35  Bedwyn                                  BUS   On time
## 11:40  Newbury                                 BUS   On time
## 12:35  Newbury                                 BUS   On time
## 12:40  Newbury                                 BUS   On time
```
