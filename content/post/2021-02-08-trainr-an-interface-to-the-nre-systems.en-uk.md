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

## Example (Last rendered on 2024-04-21 17:06)

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
## Reading (RDG) Station Board on 2024-04-21 17:06:16.99623
## Time   From                                    Plat  Expected
## 17:57  Hereford                                10    On time
## 17:58  Plymouth                                11    18:04
## 18:04  London Paddington                       7     18:07
## 18:06  Abbey Wood                              14    18:08
## 18:06  Bournemouth                             8B    On time
## 18:07  London Paddington                       9     18:10
## 18:09  Plymouth                                10    On time
## 18:21  Newbury                                 1     On time
## 18:22  Cardiff Central                         10A   On time
## 18:23  London Paddington                       9     On time
## 18:26  London Paddington                       7     On time
## 18:29  Cheltenham Spa                          10A   18:33
## 18:32  Basingstoke                             2     On time
## 18:35  Didcot Parkway                          12    On time
## 18:36  Abbey Wood                              14    18:39
## 18:40  Bristol Temple Meads                    11    On time
## 18:40  Manchester Piccadilly                   7     On time
## 18:44  Swansea                                 10    On time
## 18:45  London Paddington                       9     On time
## 18:53  London Paddington                       9     On time
## 18:56  London Paddington                       7     On time
## 18:57  Great Malvern                           10A   On time
## 18:58  Penzance                                11    19:20
## 19:03  London Paddington                       7     On time
## 19:06  Abbey Wood                              14    On time
## 19:06  Bournemouth                             8B    On time
## 19:07  London Paddington                       9     On time
## 19:10  Taunton                                 10    19:12
## 19:19  Bedwyn                                  1     On time
## 19:22  Swindon                                 10A   On time
## 19:23  London Paddington                       9     On time
## 19:25  London Paddington                       8     On time
## 19:32  Basingstoke                             2     On time
## 19:35  Didcot Parkway                          13    On time
## 19:36  Abbey Wood                              14    On time
## 19:39  Manchester Piccadilly                   7B    On time
## 19:40  Paignton                                11    19:45
## 19:44  Carmarthen                              10    On time
## 19:45  London Paddington                       9     On time
## 19:53  London Paddington                       9     On time
## 19:56  Hereford                                10    On time
## 19:57  Penzance                                11    On time
## 18:05  Bracknell                               BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:19  Guildford                               BUS   On time
## 18:23  Bracknell                               BUS   On time
## 18:35  Bracknell                               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:53  Bracknell                               BUS   On time
## 18:57  Guildford                               BUS   On time
## 19:05  Bracknell                               BUS   On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:23  Bracknell                               BUS   On time
## 19:35  Bracknell                               BUS   On time
## 19:35  Guildford                               BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
## 19:53  Bracknell                               BUS   On time
## 20:05  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-04-21 17:06:20.770617
## Time   To                                      Plat  Expected
## 18:05  London Paddington                       10    On time
## 18:07  London Paddington                       11    On time
## 18:10  Swansea                                 7     On time
## 18:13  London Paddington                       10    On time
## 18:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 18:15  Great Malvern                           9     On time
## 18:23  London Paddington                       10A   On time
## 18:25  Plymouth                                9     On time
##        via Bristol                             
## 18:26  Didcot Parkway                          12A   On time
## 18:28  Penzance                                7     On time
## 18:32  Abbey Wood                              14    On time
## 18:35  London Paddington                       10A   On time
## 18:37  Basingstoke                             2     On time
## 18:43  Newbury                                 1     On time
## 18:44  London Paddington                       11    On time
## 18:46  London Paddington                       10    On time
## 18:46  Swindon                                 9     On time
## 18:52  Bournemouth                             7     On time
## 18:55  Weston-super-Mare                       9     On time
## 19:01  Plymouth                                7     On time
## 19:02  Abbey Wood                              14    On time
## 19:05  London Paddington                       10A   On time
## 19:07  London Paddington                       11    19:21
## 19:09  Swansea                                 7     On time
## 19:12  London Paddington                       10    19:12
## 19:12  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 19:15  Worcester Shrub Hill                    9     On time
## 19:23  London Paddington                       10A   On time
## 19:25  Bristol Temple Meads                    9     On time
## 19:26  Didcot Parkway                          12A   On time
## 19:28  Plymouth                                8     On time
## 19:32  Abbey Wood                              14    On time
## 19:37  Basingstoke                             2     On time
## 19:43  Bedwyn                                  1     On time
## 19:44  London Paddington                       11    19:46
## 19:46  London Paddington                       10    On time
## 19:46  Swindon                                 9     On time
## 19:52  Bournemouth                             7B    On time
## 19:55  Bristol Temple Meads                    9     On time
## 20:02  Abbey Wood                              14    On time
## 20:05  London Paddington                       10    On time
## 20:05  London Paddington                       11    On time
## 18:18  Bracknell                               BUS   On time
## 18:25  Guildford                               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:31  Bracknell                               BUS   On time
## 18:48  Bracknell                               BUS   On time
## 18:58  Guildford                               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:01  Bracknell                               BUS   On time
## 19:18  Bracknell                               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:31  Bracknell                               BUS   On time
## 19:36  Guildford                               BUS   On time
## 19:48  Bracknell                               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:01  Bracknell                               BUS   On time
```
