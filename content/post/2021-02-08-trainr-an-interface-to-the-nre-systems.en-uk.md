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

## Example (Last rendered on 2023-03-05 12:03)

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
## Reading (RDG) Station Board on 2023-03-05 12:03:28
## Time   From                                    Plat  Expected
## 11:56  Great Malvern                           10A   On time
## 12:03  Abbey Wood                              15    On time
## 12:07  London Paddington                       8     On time
## 12:07  Plymouth                                11    12:15
## 12:10  Didcot Parkway                          14    On time
## 12:12  London Paddington                       9     12:14
## 12:13  London Paddington                       12    On time
## 12:14  Bristol Temple Meads                    10    On time
## 12:25  Oxford                                  10    On time
## 12:31  Cheltenham Spa                          10    On time
## 12:32  Basingstoke                             2     On time
## 12:33  Abbey Wood                              14    On time
## 12:39  Manchester Piccadilly                   12    On time
## 12:44  Swansea                                 10    On time
## 12:47  London Paddington                       9     On time
## 12:47  Salisbury                               1     On time
## 12:53  London Paddington                       9     On time
## 12:56  Great Malvern                           10A   On time
## 13:03  Abbey Wood                              14    On time
## 13:06  Bournemouth                             8     On time
## 13:06  London Paddington                       7     On time
## 13:09  Weston-super-Mare                       10    On time
## 13:10  Didcot Parkway                          15    On time
## 13:12  London Paddington                       9     On time
## 13:13  London Paddington                       13    On time
## 13:21  Bristol Parkway                         10    On time
## 13:25  Penzance                                11    On time
## 13:28  Oxford                                  10    On time
## 13:32  Basingstoke                             2     On time
## 13:33  Abbey Wood                              14    On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:44  Swansea                                 10    On time
## 13:47  London Paddington                       8     On time
## 13:47  Salisbury                               1     On time
## 13:53  London Paddington                       9     On time
## 13:55  Great Malvern                           10    On time
## 12:04  Guildford                               BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:07  Bedwyn                                  BUS   On time
## 12:09  Ascot                                   BUS   On time
## 12:23  Ascot                                   BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 12:39  Ascot                                   BUS   On time
## 12:40  Guildford                               BUS   On time
## 12:46  Newbury                                 BUS   On time
## 12:53  Ascot                                   BUS   On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:09  Ascot                                   BUS   On time
## 13:18  Guildford                               BUS   On time
## 13:23  Ascot                                   BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
## 13:39  Ascot                                   BUS   On time
## 13:53  Ascot                                   BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-05 12:03:34
## Time   To                                      Plat  Expected
## 12:02  London Paddington                       10A   On time
## 12:03  Penzance                                8     On time
## 12:10  London Paddington                       11    12:16
## 12:10  Swansea                                 8     On time
## 12:12  Salisbury                               1     On time
## 12:14  Ealing Broadway                         14    On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:16  London Paddington                       10    On time
## 12:18  Hereford                                9     On time
## 12:24  Abbey Wood                              15    On time
## 12:26  Didcot Parkway                          12    On time
## 12:26  London Paddington                       10    On time
## 12:33  London Paddington                       10    On time
## 12:37  Basingstoke                             2     On time
## 12:46  London Paddington                       10    On time
## 12:49  Oxford                                  9     On time
## 12:54  Abbey Wood                              14    On time
## 12:55  Weston-super-Mare                       9     On time
## 13:00  London Paddington                       10A   On time
## 13:03  Plymouth                                9     On time
## 13:10  Swansea                                 7     On time
## 13:11  London Paddington                       10    On time
## 13:12  Yeovil Pen Mill                         1     On time
## 13:14  Ealing Broadway                         15    On time
## 13:14  Great Malvern                           9     On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:23  London Paddington                       10    On time
## 13:24  Abbey Wood                              14    On time
## 13:26  Didcot Parkway                          13    On time
## 13:28  London Paddington                       11    On time
## 13:30  London Paddington                       10    On time
## 13:37  Basingstoke                             2     On time
## 13:46  London Paddington                       10    On time
## 13:49  Oxford                                  8     On time
## 13:52  Bournemouth                             7     On time
## 13:54  Abbey Wood                              14    On time
## 13:55  Bristol Temple Meads                    9     On time
## 14:00  London Paddington                       10    On time
## 12:16  Ascot                                   BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:31  Ascot                                   BUS   On time
## 12:43  Newbury                                 BUS   On time
## 12:45  Guildford                               BUS   On time
## 12:46  Ascot                                   BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:01  Ascot                                   BUS   On time
## 13:16  Ascot                                   BUS   On time
## 13:23  Guildford                               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:31  Ascot                                   BUS   On time
## 13:43  Bedwyn                                  BUS   On time
## 13:46  Ascot                                   BUS   On time
## 13:56  Guildford                               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:01  Ascot                                   BUS   On time
```
