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

## Example (Last rendered on 2021-09-19 18:03)

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
## Reading (RDG) Station Board on 2021-09-19 18:03:22
## Time   From                                    Plat  Expected
## 18:53  London Paddington                       9     19:01
## 18:57  Great Malvern                           10    On time
## 18:58  Penzance                                11    19:04
## 19:01  London Paddington                       8     Delayed
## 19:06  Paignton                                10    19:03
## 19:08  London Waterloo                         4     19:02
## 19:09  Bournemouth                             7     On time
## 19:12  London Paddington                       9     On time
## 19:14  Didcot Parkway                          15    On time
## 19:14  London Paddington                       13    On time
## 19:15  London Paddington                       12    On time
## 19:19  Bedwyn                                  1     19:23
## 19:26  London Paddington                       8     On time
## 19:34  Basingstoke                             2     19:40
## 19:38  London Waterloo                         6     On time
## 19:39  Oxford                                  7B    On time
## 19:40  Bristol Temple Meads                    10    On time
## 19:40  Exeter St Davids                        -     Cancelled
## 19:42  London Paddington                       9     On time
## 19:44  London Paddington                       14    On time
## 19:48  Swansea                                 10    On time
## 19:53  London Paddington                       9     On time
## 19:57  Hereford                                10    On time
## 19:58  Penzance                                11    On time
## 20:01  London Paddington                       8     On time
## 20:08  London Waterloo                         4     On time
## 20:12  London Paddington                       9     On time
## 20:13  Didcot Parkway                          15    On time
## 20:14  London Paddington                       14    On time
## 20:18  London Paddington                       13    On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:33  Basingstoke                             2     On time
## 20:38  London Waterloo                         6     On time
## 20:39  Oxford                                  8     On time
## 20:40  Plymouth                                11    On time
## 20:44  London Paddington                       14    On time
## 20:49  Swansea                                 10    On time
## 20:53  London Paddington                       9     On time
## 20:57  Great Malvern                           10    On time
## 20:58  Penzance                                11    On time
## 19:08  Guildford                               BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
## 19:51  Guildford                               BUS   On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 20:40  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-09-19 18:03:24
## Time   To                                      Plat  Expected
## 18:56  Weston-super-Mare                       9     19:03
## 19:00  London Paddington                       11    19:05
## 19:02  London Paddington                       10    On time
## 19:09  Bristol Parkway                         8     Delayed
## 19:14  Ealing Broadway                         15    On time
## 19:14  Hereford                                9     On time
## 19:15  London Paddington                       10    On time
## 19:15  Oxford                                  7     On time
## 19:21  London Waterloo                         4     On time
## 19:25  Didcot Parkway                          12    On time
## 19:27  Plymouth                                8     On time
## 19:30  Ealing Broadway                         13    On time
## 19:38  Basingstoke                             2     On time
## 19:42  London Paddington                       -     Cancelled
## 19:44  Bedwyn                                  1     On time
## 19:45  London Paddington                       10    On time
## 19:47  Oxford                                  9     On time
## 19:50  London Paddington                       10    On time
## 19:51  London Waterloo                         6     On time
## 19:52  Bournemouth                             7B    On time
## 19:56  Bristol Temple Meads                    9     On time
## 20:00  Ealing Broadway                         14    On time
## 20:00  London Paddington                       11    On time
## 20:02  London Paddington                       10    On time
## 20:09  Swansea                                 8     On time
## 20:14  Ealing Broadway                         15    On time
## 20:14  Great Malvern                           9     On time
## 20:15  Oxford                                  3     On time
## 20:21  London Waterloo                         4     On time
## 20:25  Didcot Parkway                          13    On time
## 20:30  Ealing Broadway                         14    On time
## 20:33  Plymouth                                7     On time
## 20:38  Basingstoke                             2     On time
## 20:40  London Paddington                       11    On time
## 20:42  Newbury                                 1     On time
## 20:50  London Paddington                       10    On time
## 20:51  London Waterloo                         6     On time
## 20:52  Bournemouth                             8     On time
## 20:55  Weston-super-Mare                       9     On time
## 21:00  Ealing Broadway                         14    On time
## 21:00  London Paddington                       11    On time
## 21:02  London Paddington                       10    On time
## 19:35  Guildford                               BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 20:10  Guildford                               BUS   On time
## 20:35  Guildford                               BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
