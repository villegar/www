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

## Example (Last rendered on 2021-03-06 14:08)

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
## Reading (RDG) Station Board on 2021-03-06 14:08:29
## Time   From                                    Plat  Expected
## 13:46  Port Talbot Parkway                     -     Delayed
## 13:56  London Paddington                       -     14:00
## 13:59  Penzance                                -     14:08
## 14:02  Didcot Parkway                          -     13:59
## 14:11  London Paddington                       -     On time
## 14:13  London Paddington                       -     14:05
## 14:16  London Paddington                       -     On time
## 14:23  Bedwyn                                  -     On time
## 14:26  London Paddington                       -     Delayed
## 14:31  London Paddington                       -     On time
## 14:33  Cheltenham Spa                          -     14:47
## 14:33  Redhill                                 -     On time
## 14:40  Bristol Temple Meads                    -     14:53
## 14:40  Manchester Piccadilly                   -     On time
## 14:42  Newbury                                 -     On time
## 14:43  London Paddington                       -     On time
## 14:44  London Paddington                       -     On time
## 14:46  Port Talbot Parkway                     -     15:04
## 14:53  London Paddington                       -     On time
## 14:53  Worcester Foregate Street               -     On time
## 14:56  London Paddington                       -     On time
## 14:57  Basingstoke                             -     On time
## 14:59  London Paddington                       -     On time
## 15:00  Plymouth                                -     On time
## 15:01  Didcot Parkway                          -     On time
## 15:10  Bournemouth                             -     On time
## 15:11  London Paddington                       -     On time
## 15:13  London Paddington                       -     On time
## 15:16  London Paddington                       -     On time
## 15:21  Bedwyn                                  -     On time
## 15:27  London Paddington                       -     On time
## 15:31  Cheltenham Spa                          -     Delayed
## 15:32  London Paddington                       -     On time
## 15:33  Redhill                                 -     On time
## 15:38  Newbury                                 -     On time
## 15:39  Manchester Piccadilly                   -     On time
## 15:40  Bristol Temple Meads                    -     On time
## 15:43  London Paddington                       -     On time
## 15:44  London Paddington                       -     On time
## 15:47  Port Talbot Parkway                     -     16:17
## 15:53  London Paddington                       -     On time
## 15:54  Hereford                                -     On time
## 15:57  Basingstoke                             -     On time
## 14:12  Ascot                                   -     On time
## 14:27  Ascot                                   -     On time
## 14:42  Ascot                                   -     On time
## 14:57  Ascot                                   -     On time
## 15:12  Ascot                                   -     On time
## 15:27  Ascot                                   -     On time
## 15:42  Ascot                                   -     On time
## 15:57  Ascot                                   -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-06 14:08:32
## Time   To                                      Plat  Expected
## 13:48  London Paddington                       -     Delayed
## 13:58  Cheltenham Spa                          -     14:08
## 14:05  London Paddington                       -     14:09
## 14:09  Newbury                                 -     On time
## 14:13  Port Talbot Parkway                     -     On time
## 14:15  Ealing Broadway                         -     On time
## 14:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 14:19  Great Malvern                           -     On time
## 14:20  Redhill                                 -     On time
## 14:22  Ealing Broadway                         -     On time
## 14:24  London Paddington                       -     On time
## 14:28  Penzance                                -     Delayed
## 14:34  Bedwyn                                  -     On time
## 14:35  London Paddington                       -     14:48
## 14:41  London Paddington                       -     15:00
## 14:48  London Paddington                       -     15:05
## 14:49  Bournemouth                             -     On time
## 14:52  Basingstoke                             -     On time
## 14:52  Ealing Broadway                         -     On time
## 14:53  Didcot Parkway                          -     On time
## 14:55  Bristol Temple Meads                    -     On time
## 14:56  London Paddington                       -     On time
## 14:58  Cheltenham Spa                          -     On time
## 15:01  Plymouth                                -     On time
## 15:05  London Paddington                       -     On time
## 15:10  Newbury                                 -     On time
## 15:13  Port Talbot Parkway                     -     On time
## 15:15  Ealing Broadway                         -     On time
## 15:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 15:19  Great Malvern                           -     On time
## 15:20  Redhill                                 -     On time
## 15:22  Ealing Broadway                         -     On time
## 15:23  London Paddington                       -     On time
## 15:29  Penzance                                -     On time
## 15:34  Bedwyn                                  -     On time
## 15:35  London Paddington                       -     Delayed
## 15:41  London Paddington                       -     On time
## 15:50  London Paddington                       -     16:18
## 15:52  Basingstoke                             -     On time
## 15:52  Ealing Broadway                         -     On time
## 15:53  Didcot Parkway                          -     On time
## 15:55  Bristol Temple Meads                    -     On time
## 15:56  London Paddington                       -     On time
## 14:17  Ascot                                   -     On time
## 14:32  Ascot                                   -     On time
## 14:47  Ascot                                   -     On time
## 15:02  Ascot                                   -     On time
## 15:17  Ascot                                   -     On time
## 15:32  Ascot                                   -     On time
## 15:47  Ascot                                   -     On time
## 16:02  Ascot                                   -     On time
```
