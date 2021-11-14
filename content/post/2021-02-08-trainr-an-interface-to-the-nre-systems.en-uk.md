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

## Example (Last rendered on 2021-11-14 12:03)

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
## Reading (RDG) Station Board on 2021-11-14 12:03:47
## Time   From                                    Plat  Expected
## 11:57  Great Malvern                           10A   On time
## 11:57  Plymouth                                11    12:01
## 12:06  London Paddington                       9     On time
## 12:09  Bristol Temple Meads                    11    12:14
## 12:11  Didcot Parkway                          15    On time
## 12:12  London Paddington                       9     12:17
## 12:12  London Paddington                       14    On time
## 12:19  Newbury                                 1     On time
## 12:22  London Waterloo                         6     On time
## 12:23  London Paddington                       13    On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          10    On time
## 12:33  Basingstoke                             2     On time
## 12:39  Manchester Piccadilly                   13    12:44
## 12:43  Swansea                                 11    On time
## 12:44  London Paddington                       14    On time
## 12:50  London Paddington                       9     On time
## 12:52  London Waterloo                         4     On time
## 12:55  Plymouth                                11    On time
## 12:57  Oxford                                  10    On time
## 13:01  London Paddington                       8     On time
## 13:06  London Paddington                       9     On time
## 13:07  Eastleigh                               13    On time
## 13:09  Weston-super-Mare                       11    On time
## 13:10  Didcot Parkway                          15    On time
## 13:12  London Paddington                       8     On time
## 13:12  London Paddington                       14    On time
## 13:17  Bedwyn                                  1     On time
## 13:22  London Paddington                       13    On time
## 13:22  London Waterloo                         6     On time
## 13:26  London Paddington                       7     On time
## 13:26  Paignton                                11    On time
## 13:33  Basingstoke                             2     On time
## 13:39  Manchester Piccadilly                   7     Delayed
## 13:40  Bristol Temple Meads                    11    On time
## 13:42  London Paddington                       14    On time
## 13:43  Bristol Parkway                         10    On time
## 13:50  London Paddington                       9     On time
## 13:52  London Waterloo                         4     On time
## 13:58  Plymouth                                11    On time
## 12:21  Heathrow Central Bus Stn                BUS   On time
## 12:43  Guildford                               BUS   On time
## 13:13  Guildford                               BUS   On time
## 13:21  Heathrow Central Bus Stn                BUS   On time
## 13:54  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-14 12:03:50
## Time   To                                      Plat  Expected
## 12:00  London Paddington                       11    12:03
## 12:05  London Paddington                       10A   On time
## 12:09  Carmarthen                              9     On time
## 12:12  London Paddington                       11    12:15
## 12:13  Ealing Broadway                         15    On time
## 12:14  Hereford                                9     12:18
## 12:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 12:21  London Waterloo                         4     On time
## 12:22  Ealing Broadway                         14    On time
## 12:25  Didcot Parkway                          13    On time
## 12:30  Plymouth                                7     On time
## 12:38  Basingstoke                             2     On time
## 12:40  London Paddington                       10    On time
## 12:44  Newbury                                 1     On time
## 12:46  London Paddington                       11    On time
## 12:51  London Waterloo                         6     On time
## 12:52  Ealing Broadway                         14    On time
## 12:55  Weston-super-Mare                       9     On time
## 13:00  London Paddington                       11    On time
## 13:03  Exeter St Davids                        8     On time
## 13:05  London Paddington                       10    On time
## 13:09  Swansea                                 9     On time
## 13:12  Ealing Broadway                         15    On time
## 13:12  London Paddington                       11    On time
## 13:14  Great Malvern                           8     On time
## 13:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 13:21  London Waterloo                         4     On time
## 13:22  Ealing Broadway                         14    On time
## 13:25  Didcot Parkway                          13    On time
## 13:29  Plymouth                                7     On time
## 13:30  London Paddington                       11    On time
## 13:38  Basingstoke                             2     On time
## 13:42  London Paddington                       11    On time
## 13:44  Bedwyn                                  1     On time
## 13:46  London Paddington                       10    On time
## 13:51  London Waterloo                         6     On time
## 13:52  Ealing Broadway                         14    On time
## 13:52  Eastleigh                               7     Delayed
## 13:55  Bristol Temple Meads                    9     On time
## 14:00  London Paddington                       11    On time
## 12:05  Guildford                               BUS   On time
## 12:45  Guildford                               BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
## 13:30  Guildford                               BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
```
