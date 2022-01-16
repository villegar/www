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

## Example (Last rendered on 2022-01-16 18:03)

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
## Reading (RDG) Station Board on 2022-01-16 18:03:45
## Time   From                                    Plat  Expected
## 17:24  Swansea                                 10    18:09
## 17:57  Plymouth                                11    18:01
## 18:09  Hereford                                10    18:15
## 18:12  London Paddington                       9     18:14
## 18:13  Didcot Parkway                          15    On time
## 18:13  London Paddington                       7B    18:15
## 18:13  London Paddington                       14    On time
## 18:15  London Paddington                       12    On time
## 18:22  Newbury                                 1     On time
## 18:24  Carmarthen                              11    18:27
## 18:27  London Paddington                       7     On time
## 18:29  Didcot Parkway                          10    On time
## 18:31  London Paddington                       8     On time
## 18:33  Basingstoke                             2     On time
## 18:36  Bristol Temple Meads                    11    18:38
## 18:43  London Paddington                       14    On time
## 18:47  Manchester Piccadilly                   9     On time
## 18:50  London Paddington                       8     On time
## 18:57  Penzance                                11    On time
## 19:00  London Paddington                       7     On time
## 19:02  Bournemouth                             8     On time
## 19:09  Great Malvern                           10    On time
## 19:12  London Paddington                       8B    On time
## 19:13  London Paddington                       13    On time
## 19:13  London Paddington                       7     On time
## 19:14  Didcot Parkway                          14    On time
## 19:15  London Paddington                       12    On time
## 19:22  Bedwyn                                  1     On time
## 19:27  London Paddington                       8     On time
## 19:28  Swansea                                 11    On time
## 19:29  Didcot Parkway                          10    On time
## 19:31  London Paddington                       7     On time
## 19:34  Basingstoke                             2     On time
## 19:38  Bristol Temple Meads                    -     Cancelled
## 19:43  London Paddington                       14    On time
## 19:43  Newton Abbot                            11    On time
## 19:47  Manchester Piccadilly                   7     On time
## 19:50  London Paddington                       8     On time
## 19:57  Plymouth                                11    On time
## 18:02  Guildford                               BUS   On time
## 18:07  Swindon                                 BUS   On time
## 18:14  Bracknell                               BUS   On time
## 18:21  Heathrow Central Bus Stn                BUS   On time
## 18:30  Bracknell                               BUS   On time
## 18:44  Bracknell                               BUS   On time
## 18:45  Guildford                               BUS   On time
## 18:45  Swindon                                 BUS   On time
## 19:00  Bracknell                               BUS   On time
## 19:07  Swindon                                 BUS   On time
## 19:14  Bracknell                               BUS   On time
## 19:18  Guildford                               BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
## 19:30  Bracknell                               BUS   On time
## 19:35  Swindon                                 BUS   On time
## 19:44  Bracknell                               BUS   On time
## 20:00  Bracknell                               BUS   On time
## 20:02  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-16 18:03:50
## Time   To                                      Plat  Expected
## 17:27  London Paddington                       10    18:10
## 17:59  London Paddington                       11    18:03
## 18:07  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:10  London Paddington                       10    18:16
## 18:14  Ealing Broadway                         15    On time
## 18:14  Great Malvern                           9     18:15
## 18:18  Bristol Temple Meads                    7B    On time
## 18:22  Ealing Broadway                         14    On time
## 18:25  Didcot Parkway                          12    On time
## 18:27  London Paddington                       11    18:27
## 18:29  Penzance                                7     On time
## 18:30  London Paddington                       10    On time
## 18:33  Swansea                                 8     On time
## 18:39  Basingstoke                             2     On time
## 18:42  London Paddington                       11    On time
## 18:44  Newbury                                 1     On time
## 18:52  Didcot Parkway                          8     On time
## 18:52  Ealing Broadway                         14    On time
## 18:59  London Paddington                       11    On time
## 19:02  Plymouth                                7     On time
## 19:07  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:10  London Paddington                       10    On time
## 19:14  Ealing Broadway                         14    On time
## 19:14  Worcester Shrub Hill                    8B    On time
## 19:18  Bristol Temple Meads                    7     On time
## 19:22  Ealing Broadway                         13    On time
## 19:25  Didcot Parkway                          12    On time
## 19:29  Plymouth                                8     On time
## 19:30  London Paddington                       11    On time
## 19:32  London Paddington                       10    On time
## 19:35  Swansea                                 7     On time
## 19:38  Basingstoke                             2     On time
## 19:42  London Paddington                       -     Cancelled
## 19:44  Bedwyn                                  1     On time
## 19:45  London Paddington                       11    On time
## 19:52  Bournemouth                             7     On time
## 19:52  Didcot Parkway                          8     On time
## 19:52  Ealing Broadway                         14    On time
## 19:59  London Paddington                       11    On time
## 18:06  Bracknell                               BUS   On time
## 18:10  Swindon                                 BUS   On time
## 18:21  Bracknell                               BUS   On time
## 18:25  Swindon                                 BUS   On time
## 18:35  Guildford                               BUS   On time
## 18:36  Bracknell                               BUS   On time
## 18:51  Bracknell                               BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
## 19:06  Bracknell                               BUS   On time
## 19:10  Swindon                                 BUS   On time
## 19:18  Guildford                               BUS   On time
## 19:21  Bracknell                               BUS   On time
## 19:25  Swindon                                 BUS   On time
## 19:36  Bracknell                               BUS   On time
## 19:51  Bracknell                               BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 20:01  Guildford                               BUS   On time
```
