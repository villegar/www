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

## Example (Last rendered on 2022-01-09 20:03)

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
## Reading (RDG) Station Board on 2022-01-09 20:03:28
## Time   From                                    Plat  Expected
## 19:48  London Paddington                       9B    20:12
## 19:57  Plymouth                                11    20:08
## 20:12  London Paddington                       9     20:22
## 20:13  Didcot Parkway                          15    On time
## 20:13  London Paddington                       7B    Delayed
## 20:13  London Paddington                       14    On time
## 20:15  London Paddington                       13    20:18
## 20:22  Newbury                                 1     On time
## 20:24  Carmarthen                              -     Cancelled
## 20:25  Oxford                                  9B    On time
## 20:27  London Paddington                       7B    20:33
## 20:29  Bristol Temple Meads                    -     Cancelled
## 20:33  Basingstoke                             2     20:41
## 20:39  Manchester Piccadilly                   8     On time
## 20:42  Plymouth                                11    On time
## 20:43  London Paddington                       14    On time
## 20:48  London Paddington                       9B    On time
## 20:56  Great Malvern                           10A   On time
## 20:57  Penzance                                11    On time
## 21:07  Bournemouth                             8     On time
## 21:12  London Paddington                       9     On time
## 21:13  Didcot Parkway                          13    On time
## 21:13  London Paddington                       7     On time
## 21:13  London Paddington                       14    On time
## 21:15  London Paddington                       12    On time
## 21:18  Swansea                                 11A   21:21
## 21:28  London Paddington                       7B    On time
## 21:29  Bedwyn                                  10    On time
## 21:34  Basingstoke                             -     Cancelled
## 21:37  Bristol Temple Meads                    11A   On time
## 21:37  London Paddington                       7B    On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:40  London Paddington                       9B    On time
## 21:43  London Paddington                       14    On time
## 21:57  Great Malvern                           10A   On time
## 20:02  Guildford                               BUS   On time
## 20:03  Bracknell                               BUS   On time
## 20:07  Swindon                                 BUS   On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 20:19  Bracknell                               BUS   On time
## 20:33  Bracknell                               BUS   On time
## 20:35  Swindon                                 BUS   On time
## 20:45  Guildford                               BUS   On time
## 20:49  Bracknell                               BUS   On time
## 21:03  Bracknell                               BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
## 21:07  Swindon                                 BUS   On time
## 21:18  Guildford                               BUS   On time
## 21:19  Bracknell                               BUS   On time
## 21:33  Bracknell                               BUS   On time
## 21:35  Swindon                                 BUS   On time
## 21:49  Bracknell                               BUS   On time
## 22:02  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-09 20:03:32
## Time   To                                      Plat  Expected
## 19:50  Oxford                                  9B    20:13
## 19:59  London Paddington                       11    20:07
## 20:14  Great Malvern                           9     20:23
## 20:14  London Paddington                       15    On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:18  Bristol Temple Meads                    7B    Delayed
## 20:27  Ealing Broadway                         14    On time
## 20:29  Plymouth                                7B    20:34
## 20:30  Didcot Parkway                          13    On time
## 20:30  London Paddington                       -     Cancelled
## 20:32  London Paddington                       9B    On time
## 20:38  Basingstoke                             -     Cancelled
## 20:42  Newbury                                 1     On time
## 20:45  London Paddington                       -     Cancelled
## 20:50  London Paddington                       11    On time
## 20:50  Oxford                                  9B    On time
## 20:52  Bournemouth                             8     On time
## 20:57  Ealing Broadway                         14    On time
## 20:59  London Paddington                       11    On time
## 21:01  London Paddington                       10A   On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:14  Ealing Broadway                         13    On time
## 21:15  Didcot Parkway                          12    On time
## 21:15  Swansea                                 7     On time
## 21:15  Worcester Shrub Hill                    9     On time
## 21:20  London Paddington                       11A   21:22
## 21:30  Ealing Broadway                         14    On time
## 21:33  Exeter St Davids                        7B    On time
## 21:38  Basingstoke                             2     On time
## 21:42  Bristol Temple Meads                    7B    On time
## 21:45  Bedwyn                                  10    On time
## 21:45  London Paddington                       11A   On time
## 21:48  Oxford                                  9B    On time
## 21:52  Southampton Central                     8     On time
## 21:57  Ealing Broadway                         14    On time
## 21:59  London Paddington                       10A   On time
## 20:10  Swindon                                 BUS   On time
## 20:16  Bracknell                               BUS   On time
## 20:25  Guildford                               BUS   On time
## 20:25  Swindon                                 BUS   On time
## 20:31  Bracknell                               BUS   On time
## 20:46  Bracknell                               BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 21:01  Bracknell                               BUS   On time
## 21:10  Swindon                                 BUS   On time
## 21:16  Bracknell                               BUS   On time
## 21:25  Swindon                                 BUS   On time
## 21:31  Bracknell                               BUS   On time
## 21:46  Bracknell                               BUS   On time
## 21:55  Guildford                               BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 22:00  Swindon                                 BUS   On time
## 22:01  Bracknell                               BUS   On time
```
