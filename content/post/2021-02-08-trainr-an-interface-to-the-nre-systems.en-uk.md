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

## Example (Last rendered on 2022-09-11 14:03)

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
## Reading (RDG) Station Board on 2022-09-11 14:03:52
## Time   From                                    Plat  Expected
## 14:57  Penzance                                11    Delayed
## 15:00  Didcot Parkway                          10    On time
## 15:00  London Paddington                       9     15:04
## 15:05  Bournemouth                             8     15:07
## 15:08  Guildford                               6     15:12
## 15:09  Weston-super-Mare                       11    On time
## 15:10  Maidenhead                              14    On time
## 15:13  Didcot Parkway                          15    15:18
## 15:17  London Paddington                       12    On time
## 15:18  Bedwyn                                  3     On time
## 15:23  London Paddington                       9     On time
## 15:26  London Paddington                       7     On time
## 15:32  London Waterloo                         4     On time
## 15:33  Basingstoke                             2     15:49
## 15:38  Guildford                               5     On time
## 15:39  Didcot Parkway                          7     On time
## 15:39  London Paddington                       14    15:42
## 15:40  Bristol Temple Meads                    10    On time
## 15:41  Exeter St Davids                        11A   16:10
## 15:46  Swansea                                 11    16:09
## 15:47  Salisbury                               1     On time
## 15:53  London Paddington                       9     On time
## 15:58  Exeter St Davids                        11    16:35
## 16:00  Didcot Parkway                          10    On time
## 16:00  London Paddington                       9     On time
## 16:02  London Waterloo                         4     On time
## 16:08  Guildford                               6     On time
## 16:08  London Paddington                       14    On time
## 16:09  Bristol Temple Meads                    11    On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15    On time
## 16:17  London Paddington                       12    On time
## 16:23  London Paddington                       9     On time
## 16:26  London Paddington                       7     On time
## 16:32  Cheltenham Spa                          11A   On time
## 16:32  London Waterloo                         4     On time
## 16:33  Basingstoke                             2     On time
## 16:38  Guildford                               5     On time
## 16:39  Didcot Parkway                          13    On time
## 16:39  London Paddington                       14    On time
## 16:44  Swansea                                 10    On time
## 16:47  Salisbury                               1     On time
## 16:53  London Paddington                       9     On time
## 16:57  London Paddington                       7     On time
## 16:58  Penzance                                11    On time
## 17:00  Didcot Parkway                          10    On time
## 17:02  London Waterloo                         4     On time
## 15:45  Heathrow Central Bus Stn                BUS   On time
## 16:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-11 14:03:58
## Time   To                                      Plat  Expected
## 15:00  London Paddington                       11    Delayed
## 15:02  London Paddington                       10    On time
## 15:09  Swansea                                 9     On time
## 15:12  Salisbury                               3     On time
## 15:15  Didcot Parkway                          8     On time
## 15:15  London Paddington                       11    On time
## 15:20  Didcot Parkway                          12    On time
## 15:21  Guildford                               5     On time
## 15:24  London Waterloo                         4     On time
## 15:25  Bristol Temple Meads                    9     On time
## 15:28  Plymouth                                7     On time
## 15:30  Didcot Parkway                          15    On time
## 15:31  Ealing Broadway                         14    On time
## 15:38  Basingstoke                             2     On time
## 15:41  Guildford                               6     On time
## 15:43  Bedwyn                                  3     On time
## 15:43  London Paddington                       11A   16:11
## 15:45  London Paddington                       10    On time
## 15:48  London Paddington                       11    16:10
## 15:52  Bournemouth                             7     On time
## 15:54  London Waterloo                         4     On time
## 15:55  Bristol Temple Meads                    9     On time
## 16:01  Ealing Broadway                         14    On time
## 16:02  London Paddington                       10    On time
## 16:09  Swansea                                 9     On time
## 16:12  Salisbury                               1     On time
## 16:15  Didcot Parkway                          13    On time
## 16:15  London Paddington                       11    On time
## 16:20  Didcot Parkway                          12    On time
## 16:21  Guildford                               5     On time
## 16:24  Bristol Temple Meads                    9     On time
## 16:24  London Waterloo                         4     On time
## 16:28  Penzance                                7     On time
## 16:30  Didcot Parkway                          15    On time
## 16:31  Ealing Broadway                         14    On time
## 16:38  Basingstoke                             2     On time
## 16:41  Guildford                               6     On time
## 16:42  London Paddington                       11A   On time
## 16:43  Newbury                                 3     On time
## 16:46  London Paddington                       10    On time
## 16:54  London Waterloo                         4     On time
## 16:55  Plymouth                                9     On time
##        via Bristol                             
## 17:00  London Paddington                       11    On time
## 17:01  Ealing Broadway                         14    On time
## 17:02  London Paddington                       10    On time
## 17:02  Plymouth                                7     On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
```
