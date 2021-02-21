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

## Example (Last rendered on 2021-02-21 12:09)

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
## Reading (RDG) Station Board on 2021-02-21 12:09:03
## Time   From                                    Plat  Expected
## 12:09  Bristol Temple Meads                    11    12:06
## 12:10  Didcot Parkway                          15    On time
## 12:14  London Paddington                       9     On time
## 12:15  Slough                                  12    On time
## 12:20  Newbury                                 3     On time
## 12:24  London Paddington                       9     On time
## 12:26  London Paddington                       7     On time
## 12:31  London Paddington                       14    On time
## 12:32  Barnes                                  4     On time
## 12:33  Basingstoke                             2     On time
## 12:39  Manchester Piccadilly                   13    On time
## 12:45  Port Talbot Parkway                     10    On time
## 12:45  Salisbury                               1     On time
## 12:55  Penzance                                11    On time
## 12:56  London Paddington                       9     On time
## 12:57  Oxford                                  -     Cancelled
## 13:01  London Paddington                       14    On time
## 13:02  Clapham Junction                        4     On time
## 13:06  Bournemouth                             7     On time
## 13:07  Gatwick Airport                         6     On time
## 13:09  Weston-super-Mare                       11    On time
## 13:10  Didcot Parkway                          15    On time
## 13:14  London Paddington                       9     On time
## 13:15  Slough                                  12    On time
## 13:21  Bedwyn                                  3     On time
## 13:24  London Paddington                       9     On time
## 13:26  London Paddington                       7     On time
## 13:29  London Paddington                       14    On time
## 13:32  Barnes                                  4     On time
## 13:33  Basingstoke                             2     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:45  Salisbury                               1     On time
## 13:47  Port Talbot Parkway                     10    On time
## 13:56  London Paddington                       9     On time
## 13:57  Oxford                                  10    On time
## 14:01  London Paddington                       14    On time
## 14:05  Clapham Junction                        4     On time
## 14:07  Gatwick Airport                         5     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-21 12:09:05
## Time   To                                      Plat  Expected
## 12:10  Ealing Broadway                         14    On time
## 12:12  Salisbury                               1     On time
## 12:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 12:16  Port Talbot Parkway                     9     On time
## 12:19  London Paddington                       11    On time
## 12:20  Slough                                  15    On time
## 12:24  Barnes                                  4     On time
## 12:26  Didcot Parkway                          12    On time
## 12:26  Oxford                                  9     On time
## 12:27  Penzance                                7     On time
## 12:35  Newbury                                 3     On time
## 12:38  Basingstoke                             2     On time
## 12:40  Ealing Broadway                         14    On time
## 12:41  Gatwick Airport                         6     On time
##        via Guildford                           
## 12:49  London Paddington                       10    On time
## 12:54  Clapham Junction                        4     On time
## 12:57  Weston-super-Mare                       9     On time
## 13:03  London Paddington                       11    On time
## 13:05  London Paddington                       -     Cancelled
## 13:10  Ealing Broadway                         14    On time
## 13:12  Yeovil Pen Mill                         1     On time
## 13:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 13:16  Port Talbot Parkway                     9     On time
## 13:19  London Paddington                       11    On time
## 13:20  Slough                                  15    On time
## 13:24  Barnes                                  4     On time
## 13:25  Didcot Parkway                          12    On time
## 13:26  Oxford                                  9     On time
## 13:27  Plymouth                                7     On time
## 13:35  Bedwyn                                  3     On time
## 13:38  Basingstoke                             2     On time
## 13:40  Ealing Broadway                         14    On time
## 13:41  Gatwick Airport                         6     On time
##        via Guildford                           
## 13:49  London Paddington                       10    On time
## 13:52  Bournemouth                             7     On time
## 13:54  Clapham Junction                        4     On time
## 13:58  Bristol Temple Meads                    9     On time
## 14:05  London Paddington                       10    On time
```
