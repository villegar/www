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

## Example (Last rendered on 2022-10-02 08:04)

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
## Reading (RDG) Station Board on 2022-10-02 08:04:48
## Time   From                                    Plat  Expected
## 09:02  Ascot                                   4     On time
## 09:04  Didcot Parkway                          15    On time
## 09:07  London Paddington                       7     09:04
## 09:08  London Paddington                       9     On time
## 09:10  Swindon                                 10    On time
## 09:15  Newbury                                 3     On time
## 09:17  London Paddington                       12    On time
## 09:23  London Paddington                       9     On time
## 09:28  Bristol Parkway                         11    On time
## 09:33  Ascot                                   -     Cancelled
## 09:33  Basingstoke                             2     09:37
## 09:33  London Paddington                       14    On time
## 09:39  Bristol Temple Meads                    10    On time
## 09:40  Guildford                               5     On time
## 09:47  Salisbury                               1     On time
## 09:55  London Paddington                       9     On time
## 09:58  Didcot Parkway                          15    On time
## 09:58  Didcot Parkway                          11    On time
## 10:03  Ascot                                   4     On time
## 10:03  London Paddington                       14    On time
## 10:05  Southampton Central                     12B   On time
## 10:08  Guildford                               6     On time
## 10:09  Bristol Temple Meads                    10    On time
## 10:14  London Paddington                       9     On time
## 10:22  London Paddington                       13    On time
## 10:25  Bristol Parkway                         10    On time
## 10:30  Bedwyn                                  13    On time
## 10:33  Ascot                                   4     On time
## 10:33  Basingstoke                             2     On time
## 10:33  London Paddington                       14    On time
## 10:38  Guildford                               5     On time
## 10:39  Didcot Parkway                          13    On time
## 10:42  London Paddington                       9     On time
## 10:47  Salisbury                               1     On time
## 10:50  Bristol Parkway                         10    On time
## 10:53  London Paddington                       9     On time
## 10:58  Didcot Parkway                          11    On time
## 11:03  Ascot                                   4     On time
## 11:03  London Paddington                       14    On time
## 09:45  Heathrow Central Bus Stn                BUS   On time
## 10:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-02 08:04:54
## Time   To                                      Plat  Expected
## 09:06  Ealing Broadway                         15    On time
## 09:09  Didcot Parkway                          7     On time
## 09:10  Penzance                                9     On time
## 09:12  Salisbury                               1     On time
## 09:15  Didcot Parkway                          8     On time
## 09:16  London Paddington                       10    On time
## 09:18  Didcot Parkway                          12    On time
## 09:21  Guildford                               13A   On time
## 09:24  Ascot                                   4     On time
## 09:24  Ealing Broadway                         14    On time
## 09:29  Bristol Temple Meads                    9     On time
## 09:37  London Paddington                       11    On time
## 09:38  Basingstoke                             2     On time
## 09:41  Guildford                               6     On time
## 09:43  Bedwyn                                  13B   On time
## 09:45  London Paddington                       10    On time
## 09:52  Bournemouth                             8     On time
## 09:54  Ascot                                   6     On time
## 09:54  Ealing Broadway                         14    On time
## 10:03  Carmarthen                              9     On time
## 10:03  London Paddington                       11    On time
## 10:12  London Paddington                       10    On time
## 10:12  Salisbury                               1     On time
## 10:14  Ealing Broadway                         15    On time
## 10:15  Didcot Parkway                          12B   On time
## 10:20  Didcot Parkway                          9     On time
## 10:21  Guildford                               5     On time
## 10:24  Ascot                                   4     On time
## 10:24  Ealing Broadway                         14    On time
## 10:26  Didcot Parkway                          13    On time
## 10:35  London Paddington                       10    On time
## 10:38  Basingstoke                             2     On time
## 10:41  Guildford                               6     On time
## 10:43  Bristol Parkway                         9     On time
## 10:43  Newbury                                 3     On time
## 10:52  London Paddington                       10    On time
## 10:54  Ascot                                   4     On time
## 10:54  Ealing Broadway                         14    On time
## 10:55  Bristol Temple Meads                    9     On time
## 11:03  London Paddington                       11    On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
```
