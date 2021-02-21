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

## Example (Last rendered on 2021-02-21 18:09)

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
## Reading (RDG) Station Board on 2021-02-21 18:09:10
## Time   From                                    Plat  Expected
## 18:10  Bristol Temple Meads                    11    18:06
## 18:13  Didcot Parkway                          15    On time
## 18:14  London Paddington                       9     On time
## 18:14  Plymouth                                11A   On time
## 18:15  Slough                                  12    On time
## 18:24  London Paddington                       9B    On time
## 18:26  London Paddington                       7     On time
## 18:29  London Paddington                       9     On time
## 18:31  London Paddington                       14    On time
## 18:32  Barnes                                  4     On time
## 18:32  Basingstoke                             2     On time
## 18:35  Newbury                                 1     On time
## 18:39  Manchester Piccadilly                   13    On time
## 18:45  Port Talbot Parkway                     11    On time
## 18:56  London Paddington                       8     On time
## 18:57  Oxford                                  10A   On time
## 18:58  Penzance                                11    On time
## 19:01  London Paddington                       14    On time
## 19:02  Clapham Junction                        4     On time
## 19:07  Gatwick Airport                         5     On time
## 19:09  Bournemouth                             8B    On time
## 19:09  Paignton                                11    On time
## 19:14  Didcot Parkway                          15    On time
## 19:14  London Paddington                       9B    On time
## 19:15  Slough                                  12    On time
## 19:21  Bedwyn                                  1     On time
## 19:24  London Paddington                       7     On time
## 19:26  London Paddington                       9B    On time
## 19:31  London Paddington                       14    On time
## 19:32  Barnes                                  6     On time
## 19:33  Basingstoke                             2     On time
## 19:38  Exeter St Davids                        11    On time
## 19:39  Manchester Piccadilly                   8     On time
## 19:47  Port Talbot Parkway                     10    On time
## 19:52  London Paddington                       8     On time
## 19:56  London Paddington                       9     On time
## 19:57  Oxford                                  10    On time
## 20:01  London Paddington                       14    On time
## 20:01  Penzance                                11    On time
## 20:02  Clapham Junction                        4     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-21 18:09:12
## Time   To                                      Plat  Expected
## 18:10  Ealing Broadway                         14    On time
## 18:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 18:16  Cardiff Central                         9     On time
## 18:16  London Paddington                       11    On time
## 18:19  London Paddington                       11A   On time
## 18:20  Slough                                  15    On time
## 18:24  Barnes                                  4     On time
## 18:25  Didcot Parkway                          12    On time
## 18:26  Oxford                                  9B    On time
## 18:27  Penzance                                7     On time
## 18:30  Plymouth                                9     On time
##        via Bristol                             
## 18:38  Basingstoke                             2     On time
## 18:40  Ealing Broadway                         14    On time
## 18:41  Redhill                                 6     On time
## 18:49  London Paddington                       11    On time
## 18:50  Newbury                                 1     On time
## 18:54  Clapham Junction                        4     On time
## 18:57  Weston-super-Mare                       8     On time
## 19:03  London Paddington                       11    On time
## 19:05  London Paddington                       10A   On time
## 19:10  Ealing Broadway                         14    On time
## 19:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 19:16  Port Talbot Parkway                     9B    On time
## 19:19  London Paddington                       11    On time
## 19:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:20  Slough                                  15    On time
## 19:24  Barnes                                  4     On time
## 19:25  Didcot Parkway                          12    On time
## 19:26  Oxford                                  7     On time
## 19:30  Hereford                                9B    On time
## 19:35  Bedwyn                                  1     On time
## 19:38  Basingstoke                             2     On time
## 19:39  London Paddington                       11    On time
## 19:40  Ealing Broadway                         14    On time
## 19:49  London Paddington                       10    On time
## 19:52  Bournemouth                             8     On time
## 19:53  Oxford                                  8     On time
## 19:54  Clapham Junction                        6     On time
## 19:57  Bristol Temple Meads                    9     On time
## 20:03  London Paddington                       11    On time
## 20:05  London Paddington                       10    On time
```
