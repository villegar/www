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

## Example (Last rendered on 2022-04-05 18:03)

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
## Reading (RDG) Station Board on 2022-04-05 18:03:40
## Time   From                                    Plat  Expected
## 18:57  Penzance                                -     19:06
## 18:59  London Paddington                       -     On time
## 19:04  Basingstoke                             -     On time
## 19:05  Didcot Parkway                          -     On time
## 19:05  Gatwick Airport                         -     On time
## 19:10  Weston-super-Mare                       -     On time
## 19:11  London Paddington                       -     On time
## 19:13  London Paddington                       -     On time
## 19:14  London Waterloo                         -     On time
## 19:15  London Paddington                       -     On time
## 19:15  Newbury                                 -     19:17
## 19:16  Cardiff Central                         -     On time
## 19:22  Newbury                                 -     On time
## 19:25  Worcester Foregate Street               -     On time
## 19:26  London Paddington                       -     On time
## 19:28  Didcot Parkway                          -     On time
## 19:28  London Paddington                       -     On time
## 19:29  London Paddington                       -     On time
## 19:30  London Paddington                       -     On time
## 19:33  Redhill                                 -     On time
## 19:34  Basingstoke                             -     On time
## 19:34  London Paddington                       -     On time
## 19:39  Bristol Temple Meads                    -     On time
## 19:41  London Paddington                       -     On time
## 19:41  Manchester Piccadilly                   -     On time
## 19:43  London Paddington                       -     On time
## 19:43  London Waterloo                         -     On time
## 19:45  London Paddington                       -     19:47
## 19:46  Swansea                                 -     On time
## 19:53  London Paddington                       -     On time
## 19:54  Worcester Foregate Street               -     On time
## 19:55  London Paddington                       -     On time
## 19:55  Plymouth                                -     On time
## 19:56  London Paddington                       -     On time
## 19:57  Didcot Parkway                          -     On time
## 20:00  Basingstoke                             -     On time
## 20:03  Newbury                                 -     On time
## 20:04  Gatwick Airport                         -     On time
## 20:06  Bournemouth                             -     On time
## 20:09  London Paddington                       -     On time
## 20:10  Weston-super-Mare                       -     On time
## 20:11  London Paddington                       -     On time
## 20:13  London Waterloo                         -     On time
## 20:14  London Paddington                       -     On time
## 20:17  London Paddington                       -     On time
## 20:18  London Paddington                       -     On time
## 20:25  London Paddington                       -     On time
## 20:27  London Paddington                       -     On time
## 20:28  Banbury                                 -     On time
## 20:32  Cheltenham Spa                          -     On time
## 20:34  Basingstoke                             -     On time
## 20:34  Didcot Parkway                          -     On time
## 20:35  Redhill                                 -     On time
## 20:36  London Paddington                       -     On time
## 20:41  London Waterloo                         -     On time
## 20:43  London Paddington                       -     On time
## 20:43  Manchester Piccadilly                   -     On time
## 20:44  Newbury                                 -     On time
## 20:44  Swansea                                 -     On time
## 20:47  London Paddington                       -     On time
## 20:49  London Paddington                       -     On time
## 20:53  Gatwick Airport                         -     On time
## 20:53  Great Malvern                           -     On time
## 20:55  London Paddington                       -     On time
## 19:34  Heathrow Central Bus Stn                -     On time
## 20:05  Heathrow Central Bus Stn                -     On time
## 20:38  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-05 18:03:43
## Time   To                                      Plat  Expected
## 18:58  London Paddington                       -     19:07
## 19:01  Plymouth                                -     19:04
## 19:04  Ealing Broadway                         -     On time
## 19:05  Basingstoke                             -     On time
## 19:10  Newbury                                 -     On time
## 19:12  London Waterloo                         -     On time
## 19:13  London Paddington                       -     On time
## 19:13  Swansea                                 -     On time
## 19:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 19:16  Ealing Broadway                         -     On time
## 19:18  London Paddington                       -     On time
## 19:20  Redhill                                 -     On time
## 19:22  Ealing Broadway                         -     On time
## 19:25  Basingstoke                             -     On time
## 19:25  London Paddington                       -     On time
## 19:27  Bristol Temple Meads                    -     On time
## 19:27  London Paddington                       -     On time
## 19:30  Didcot Parkway                          -     On time
## 19:31  Plymouth                                -     On time
## 19:36  Bedwyn                                  -     On time
## 19:38  Ealing Broadway                         -     On time
## 19:41  London Paddington                       -     On time
## 19:42  London Waterloo                         -     On time
## 19:42  Newbury                                 -     On time
## 19:43  Swansea                                 -     On time
## 19:49  Bournemouth                             -     On time
## 19:49  London Paddington                       -     On time
## 19:52  Ealing Broadway                         -     On time
## 19:55  London Paddington                       -     On time
## 19:55  Oxford                                  -     On time
## 19:57  Basingstoke                             -     On time
## 19:57  Didcot Parkway                          -     On time
## 19:58  London Paddington                       -     On time
## 19:58  Weston-super-Mare                       -     On time
## 20:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 20:09  London Waterloo                         -     On time
## 20:10  Newbury                                 -     On time
## 20:12  London Paddington                       -     On time
## 20:13  Swansea                                 -     On time
## 20:15  Birmingham New Street                   -     On time
##        via Coventry                            
## 20:15  Ealing Broadway                         -     On time
## 20:19  Worcester Shrub Hill                    -     On time
## 20:20  Shalford                                -     On time
## 20:21  Basingstoke                             -     On time
## 20:22  Ealing Broadway                         -     On time
## 20:23  Didcot Parkway                          -     On time
## 20:27  Bristol Temple Meads                    -     On time
## 20:29  Plymouth                                -     On time
## 20:31  London Paddington                       -     On time
## 20:36  London Paddington                       -     On time
## 20:37  Newbury                                 -     On time
## 20:42  Ealing Broadway                         -     On time
## 20:42  London Waterloo                         -     On time
## 20:47  London Paddington                       -     On time
## 20:49  Oxford                                  -     On time
## 20:51  Didcot Parkway                          -     On time
## 20:52  Basingstoke                             -     On time
## 20:52  Ealing Broadway                         -     On time
## 20:56  London Paddington                       -     On time
## 20:57  Weston-super-Mare                       -     On time
## 21:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 20:00  Heathrow Central Bus Stn                -     On time
## 21:00  Heathrow Central Bus Stn                -     On time
```
