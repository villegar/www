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

## Example (Last rendered on 2022-10-02 10:06)

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
## Reading (RDG) Station Board on 2022-10-02 10:06:22
## Time   From                                    Plat  Expected
## 11:05  Bournemouth                             8     11:08
## 11:05  Bristol Temple Meads                    10    11:11
## 11:07  London Paddington                       9     On time
## 11:08  Guildford                               -     Cancelled
## 11:10  Didcot Parkway                          15A   On time
## 11:14  London Paddington                       7B    On time
## 11:14  Swansea                                 11    11:21
## 11:19  Bedwyn                                  1     On time
## 11:22  London Paddington                       12B   On time
## 11:32  Ascot                                   4     On time
## 11:33  Basingstoke                             2     On time
## 11:33  London Paddington                       14    On time
## 11:38  Guildford                               5     Delayed
## 11:39  Didcot Parkway                          7     On time
## 11:44  Swansea                                 11    On time
## 11:47  Salisbury                               1     On time
## 11:48  Plymouth                                10    On time
## 11:53  London Paddington                       9     On time
## 11:58  Didcot Parkway                          10A   On time
## 12:02  Ascot                                   4     On time
## 12:03  London Paddington                       14    On time
## 12:08  Guildford                               -     Cancelled
## 12:09  Bristol Temple Meads                    10    On time
## 12:10  Didcot Parkway                          15    On time
## 12:14  London Paddington                       7     On time
## 12:22  London Paddington                       12    On time
## 12:22  Newbury                                 1     On time
## 12:32  Ascot                                   4     On time
## 12:33  Basingstoke                             2     On time
## 12:33  London Paddington                       14    On time
## 12:38  Guildford                               5     On time
## 12:39  Didcot Parkway                          12    On time
## 12:44  Swansea                                 10    On time
## 12:47  Salisbury                               1     On time
## 12:58  Didcot Parkway                          11    On time
## 13:02  Ascot                                   4     On time
## 13:03  London Paddington                       14    On time
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 12:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-02 10:06:26
## Time   To                                      Plat  Expected
## 11:06  Plymouth                                7     On time
## 11:10  Swansea                                 9     On time
## 11:12  London Paddington                       10    On time
## 11:12  Salisbury                               1     On time
## 11:14  Ealing Broadway                         15A   On time
## 11:15  Didcot Parkway                          8     On time
## 11:20  Didcot Parkway                          7B    On time
## 11:20  London Paddington                       11    11:22
## 11:21  Guildford                               5     On time
## 11:24  Ascot                                   4     On time
## 11:24  Ealing Broadway                         14    On time
## 11:26  Didcot Parkway                          12B   On time
## 11:38  Basingstoke                             2     On time
## 11:41  Guildford                               5     On time
## 11:43  Bedwyn                                  1     On time
## 11:47  London Paddington                       11    On time
## 11:52  Bournemouth                             7     On time
## 11:52  London Paddington                       10    On time
## 11:54  Ascot                                   4     On time
## 11:54  Bristol Temple Meads                    9     On time
## 11:54  Ealing Broadway                         14    On time
## 12:03  London Paddington                       10A   On time
## 12:06  Penzance                                7     On time
## 12:10  Carmarthen                              9     On time
## 12:12  London Paddington                       10    On time
## 12:12  Salisbury                               1     On time
## 12:14  Ealing Broadway                         15    On time
## 12:15  Didcot Parkway                          13    On time
## 12:20  Didcot Parkway                          7     On time
## 12:21  Guildford                               5     On time
## 12:24  Ascot                                   4     On time
## 12:24  Ealing Broadway                         14    On time
## 12:26  Didcot Parkway                          12    On time
## 12:38  Basingstoke                             2     On time
## 12:41  Guildford                               -     Delayed
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       10    On time
## 12:54  Ascot                                   4     On time
## 12:54  Ealing Broadway                         14    On time
## 12:55  Bristol Temple Meads                    9     On time
## 13:03  London Paddington                       11    On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
