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

## Example (Last rendered on 2022-05-20 20:03)

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
## Reading (RDG) Station Board on 2022-05-20 20:03:52
## Time   From                                    Plat  Expected
## 21:00  Penzance                                -     21:02
## 21:03  Didcot Parkway                          -     On time
## 21:04  Basingstoke                             -     21:06
## 21:07  Bournemouth                             -     On time
## 21:09  Bristol Temple Meads                    -     On time
## 21:10  London Paddington                       -     On time
## 21:11  London Paddington                       -     On time
## 21:12  London Waterloo                         -     On time
## 21:13  London Paddington                       -     On time
## 21:16  London Paddington                       -     On time
## 21:20  London Paddington                       -     On time
## 21:21  Bedwyn                                  -     On time
## 21:24  Oxford                                  -     On time
## 21:25  London Paddington                       -     On time
## 21:27  London Paddington                       -     On time
## 21:28  Basingstoke                             -     On time
## 21:29  Didcot Parkway                          -     On time
## 21:29  Redhill                                 -     On time
## 21:33  Cheltenham Spa                          -     On time
## 21:36  Newbury                                 -     On time
## 21:41  London Waterloo                         -     On time
## 21:41  Manchester Piccadilly                   -     On time
## 21:42  London Paddington                       -     On time
## 21:44  Swansea                                 -     On time
## 21:45  London Paddington                       -     On time
## 21:46  London Paddington                       -     On time
## 21:51  London Paddington                       -     On time
## 21:53  Great Malvern                           -     On time
## 21:56  Gatwick Airport                         -     On time
## 21:57  Basingstoke                             -     On time
## 22:00  Paignton                                -     On time
## 22:05  Didcot Parkway                          -     On time
## 22:07  London Paddington                       -     On time
## 22:08  Exeter St Davids                        -     On time
## 22:11  London Paddington                       -     On time
## 22:11  London Paddington                       -     On time
## 22:16  London Paddington                       -     On time
## 22:16  London Paddington                       -     On time
## 22:16  Newbury                                 -     On time
## 22:20  Newbury                                 -     On time
## 22:25  Oxford                                  -     On time
## 22:26  London Paddington                       -     On time
## 22:32  Cheltenham Spa                          -     On time
## 22:34  Shalford                                -     On time
## 22:40  Basingstoke                             -     On time
## 22:41  London Waterloo                         -     On time
## 22:41  Manchester Piccadilly                   -     On time
## 22:42  London Paddington                       -     On time
## 22:43  London Paddington                       -     On time
## 22:43  Swansea                                 -     On time
## 22:45  Didcot Parkway                          -     On time
## 22:45  London Paddington                       -     On time
## 22:50  Salisbury                               -     On time
## 22:55  London Paddington                       -     On time
## 22:58  London Paddington                       -     On time
## 22:59  Worcester Foregate Street               -     On time
## 21:20  Heathrow Central Bus Stn                -     On time
## 22:30  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-05-20 20:03:57
## Time   To                                      Plat  Expected
## 21:03  London Paddington                       -     On time
## 21:07  Ealing Broadway                         -     On time
## 21:10  Newbury                                 -     On time
## 21:11  London Paddington                       -     On time
## 21:12  London Waterloo                         -     On time
## 21:13  Birmingham New Street                   -     On time
##        via Coventry                            
## 21:13  Swansea                                 -     On time
## 21:18  Great Malvern                           -     On time
## 21:22  Basingstoke                             -     On time
## 21:23  Didcot Parkway                          -     On time
## 21:23  London Paddington                       -     On time
## 21:26  London Paddington                       -     On time
## 21:27  Bristol Temple Meads                    -     On time
## 21:27  Ealing Broadway                         -     On time
## 21:29  Plymouth                                -     On time
## 21:34  Gatwick Airport                         -     On time
##        via Guildford                           
## 21:37  Ealing Broadway                         -     On time
## 21:42  London Waterloo                         -     On time
## 21:43  London Paddington                       -     On time
## 21:46  London Paddington                       -     On time
## 21:48  Oxford                                  -     On time
## 21:49  Didcot Parkway                          -     On time
## 21:52  Bournemouth                             -     On time
## 21:53  Cheltenham Spa                          -     On time
## 21:56  London Paddington                       -     On time
## 21:57  Ealing Broadway                         -     On time
## 22:05  Basingstoke                             -     On time
## 22:05  London Paddington                       -     On time
## 22:08  Ealing Broadway                         -     On time
## 22:10  London Paddington                       -     On time
## 22:10  Newbury                                 -     On time
## 22:12  London Waterloo                         -     On time
## 22:13  Swansea                                 -     On time
## 22:18  Didcot Parkway                          -     On time
## 22:18  Worcester Shrub Hill                    -     On time
## 22:20  London Paddington                       -     On time
## 22:26  London Paddington                       -     On time
## 22:27  Ealing Broadway                         -     On time
## 22:27  Plymouth                                -     On time
##        via Bristol                             
## 22:29  Basingstoke                             -     On time
## 22:35  London Paddington                       -     On time
## 22:45  Oxford                                  -     On time
## 22:46  Didcot Parkway                          -     On time
## 22:46  London Paddington                       -     On time
## 22:49  Southampton Central                     -     On time
## 22:52  Basingstoke                             -     On time
## 22:57  Ealing Broadway                         -     On time
## 22:59  Bristol Temple Meads                    -     On time
## 23:01  Bedwyn                                  -     On time
## 23:01  London Paddington                       -     On time
## 22:00  Heathrow Central Bus Stn                -     On time
## 23:00  Heathrow Central Bus Stn                -     On time
```
