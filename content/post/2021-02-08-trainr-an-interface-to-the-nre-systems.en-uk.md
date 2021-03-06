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

## Example (Last rendered on 2021-03-06 20:08)

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
## Reading (RDG) Station Board on 2021-03-06 20:08:01
## Time   From                                    Plat  Expected
## 19:46  Port Talbot Parkway                     -     Delayed
## 20:01  Didcot Parkway                          -     On time
## 20:10  Bristol Temple Meads                    -     20:07
## 20:11  London Paddington                       -     On time
## 20:13  London Paddington                       -     On time
## 20:16  London Paddington                       -     Delayed
## 20:18  Bedwyn                                  -     On time
## 20:26  London Paddington                       -     On time
## 20:33  Redhill                                 -     On time
## 20:34  Cheltenham Spa                          -     On time
## 20:38  Newbury                                 -     On time
## 20:39  Manchester Piccadilly                   -     On time
## 20:43  London Paddington                       -     On time
## 20:44  London Paddington                       -     Delayed
## 20:46  Port Talbot Parkway                     -     Delayed
## 20:54  Great Malvern                           -     On time
## 20:56  London Paddington                       -     On time
## 20:57  Basingstoke                             -     On time
## 21:01  Didcot Parkway                          -     On time
## 21:08  Bournemouth                             -     On time
## 21:08  Bristol Temple Meads                    -     On time
## 21:11  London Paddington                       -     On time
## 21:13  London Paddington                       -     On time
## 21:16  London Paddington                       -     On time
## 21:16  Penzance                                -     On time
## 21:20  Oxford                                  -     On time
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:38  Newbury                                 -     On time
## 21:39  Manchester Piccadilly                   -     On time
## 21:43  London Paddington                       -     On time
## 21:44  London Paddington                       -     On time
## 21:49  Redhill                                 -     On time
## 21:50  Port Talbot Parkway                     -     22:42
## 21:54  Worcester Foregate Street               -     On time
## 21:57  Basingstoke                             -     On time
## 20:12  Ascot                                   -     On time
## 20:27  Ascot                                   -     On time
## 20:42  Ascot                                   -     On time
## 20:57  Ascot                                   -     On time
## 21:12  Ascot                                   -     On time
## 21:27  Ascot                                   -     On time
## 21:42  Ascot                                   -     On time
## 21:57  Ascot                                   -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-06 20:08:03
## Time   To                                      Plat  Expected
## 19:48  London Paddington                       -     Delayed
## 20:10  Newbury                                 -     On time
## 20:11  London Paddington                       -     On time
## 20:13  Port Talbot Parkway                     -     On time
## 20:15  Ealing Broadway                         -     On time
## 20:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Great Malvern                           -     Delayed
## 20:20  London Paddington                       -     On time
## 20:22  Ealing Broadway                         -     On time
## 20:28  Plymouth                                -     On time
## 20:30  Banbury                                 -     On time
## 20:33  Gatwick Airport                         -     On time
##        via Guildford                           
## 20:35  London Paddington                       -     On time
## 20:48  London Paddington                       -     Delayed
## 20:49  Bournemouth                             -     On time
## 20:52  Basingstoke                             -     On time
## 20:52  Ealing Broadway                         -     On time
## 20:53  Didcot Parkway                          -     Delayed
## 20:56  London Paddington                       -     On time
## 20:58  Exeter St Davids                        -     On time
##        via Bristol                             
## 21:10  London Paddington                       -     On time
## 21:10  Newbury                                 -     On time
## 21:13  Cardiff Central                         -     On time
## 21:15  Birmingham New Street                   -     On time
##        via Coventry                            
## 21:15  Ealing Broadway                         -     On time
## 21:18  London Paddington                       -     On time
## 21:19  Oxford                                  -     On time
## 21:22  Ealing Broadway                         -     On time
## 21:30  Ealing Broadway                         -     On time
## 21:33  Gatwick Airport                         -     On time
##        via Guildford                           
## 21:35  London Paddington                       -     Cancelled
## 21:49  Bournemouth                             -     On time
## 21:51  London Paddington                       -     22:43
## 21:52  Basingstoke                             -     On time
## 21:52  Ealing Broadway                         -     On time
## 21:56  London Paddington                       -     On time
## 21:58  Didcot Parkway                          -     On time
## 20:17  Ascot                                   -     On time
## 20:32  Ascot                                   -     On time
## 20:47  Ascot                                   -     On time
## 21:02  Ascot                                   -     On time
## 21:17  Ascot                                   -     On time
## 21:32  Ascot                                   -     On time
## 21:47  Ascot                                   -     On time
## 22:02  Ascot                                   -     On time
```
