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

## Example (Last rendered on 2021-02-21 20:11)

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
## Reading (RDG) Station Board on 2021-02-21 20:11:07
## Time   From                                    Plat  Expected
## 20:07  Gatwick Airport                         5     20:10
## 20:12  Bristol Temple Meads                    11    20:50
## 20:13  Didcot Parkway                          15    On time
## 20:14  London Paddington                       9     On time
## 20:14  Slough                                  12    On time
## 20:20  Newbury                                 1     On time
## 20:24  London Paddington                       9     On time
## 20:28  London Paddington                       7B    On time
## 20:31  London Paddington                       14    On time
## 20:32  Barnes                                  6     On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   7B    On time
## 20:40  Plymouth                                11A   On time
## 20:49  Port Talbot Parkway                     10A   20:52
## 20:56  London Paddington                       8     On time
## 20:58  Oxford                                  10A   On time
## 20:58  Penzance                                11    On time
## 21:01  London Paddington                       14    On time
## 21:02  Clapham Junction                        4     On time
## 21:07  Bournemouth                             7B    On time
## 21:07  Gatwick Airport                         5     On time
## 21:12  Taunton                                 10    On time
## 21:13  Didcot Parkway                          13    On time
## 21:13  Slough                                  12    On time
## 21:14  London Paddington                       9     On time
## 21:21  Bedwyn                                  1     On time
## 21:24  London Paddington                       9B    On time
## 21:31  London Paddington                       14    On time
## 21:32  Barnes                                  6     On time
## 21:33  Basingstoke                             2     On time
## 21:39  London Paddington                       7B    On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:40  Redhill                                 15    On time
## 21:48  Port Talbot Parkway                     10    On time
## 21:56  London Paddington                       9     On time
## 21:59  Oxford                                  10    On time
## 22:01  London Paddington                       14    On time
## 22:02  Clapham Junction                        6     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-21 20:11:09
## Time   To                                      Plat  Expected
## 20:10  Ealing Broadway                         14    On time
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 20:16  Port Talbot Parkway                     9     On time
## 20:19  London Paddington                       11    20:51
## 20:20  Slough                                  15    On time
## 20:24  Barnes                                  4     On time
## 20:25  Didcot Parkway                          12    On time
## 20:26  Oxford                                  9     On time
## 20:29  Plymouth                                7B    On time
## 20:38  Basingstoke                             2     On time
## 20:40  Ealing Broadway                         14    On time
## 20:42  London Paddington                       11A   On time
## 20:42  Newbury                                 1     On time
## 20:50  London Paddington                       10A   20:53
## 20:52  Bournemouth                             7B    On time
## 20:54  Clapham Junction                        6     On time
## 20:57  Weston-super-Mare                       8     On time
## 21:03  London Paddington                       11    On time
## 21:05  London Paddington                       10A   On time
## 21:10  Ealing Broadway                         14    On time
## 21:12  Birmingham New Street                   7B    On time
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Didcot Parkway                          12    On time
## 21:16  Cardiff Central                         9     On time
## 21:19  London Paddington                       10    On time
## 21:20  Slough                                  13    On time
## 21:24  Barnes                                  4     On time
## 21:26  Oxford                                  9B    On time
## 21:38  Basingstoke                             2     On time
## 21:40  Ealing Broadway                         14    On time
## 21:42  Exeter St Davids                        7B    On time
## 21:46  Bedwyn                                  1     On time
## 21:50  London Paddington                       10    On time
## 21:52  Southampton Central                     7B    On time
## 21:54  Clapham Junction                        6     On time
## 21:57  Bristol Temple Meads                    9     On time
## 22:05  London Paddington                       10    On time
```
