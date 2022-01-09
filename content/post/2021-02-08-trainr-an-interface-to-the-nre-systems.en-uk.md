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

## Example (Last rendered on 2022-01-09 10:03)

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
## Reading (RDG) Station Board on 2022-01-09 10:03:27
## Time   From                                    Plat  Expected
## 09:58  Didcot Parkway                          15    On time
## 09:59  Worcester Foregate Street               10A   10:01
## 10:08  Southampton Central                     12B   10:11
## 10:10  London Paddington                       9B    On time
## 10:13  London Paddington                       7     10:16
## 10:13  London Paddington                       14    On time
## 10:15  London Paddington                       13    10:17
## 10:20  Bedwyn                                  3     On time
## 10:21  Swansea                                 11    10:29
## 10:27  London Paddington                       7     On time
## 10:27  Weston-super-Mare                       10    On time
## 10:31  London Paddington                       8     On time
## 10:33  Basingstoke                             2     On time
## 10:35  Didcot Parkway                          15    On time
## 10:39  Birmingham New Street                   13    On time
## 10:43  Exeter St Davids                        11    12:02
## 10:43  London Paddington                       14    On time
## 10:47  Salisbury                               1     On time
## 10:57  Great Malvern                           10    On time
## 11:00  London Paddington                       -     Cancelled
## 11:08  Bournemouth                             7     On time
## 11:10  Didcot Parkway                          15    On time
## 11:12  London Paddington                       9B    On time
## 11:13  London Paddington                       8     On time
## 11:13  London Paddington                       14    On time
## 11:15  London Paddington                       12    On time
## 11:22  Bedwyn                                  1     On time
## 11:23  Swansea                                 11    11:25
## 11:27  London Paddington                       7     On time
## 11:28  Bristol Temple Meads                    10    On time
## 11:31  London Paddington                       8     On time
## 11:33  Basingstoke                             2     On time
## 11:39  Manchester Piccadilly                   7     On time
## 11:39  Plymouth                                11    On time
## 11:43  London Paddington                       14    On time
## 11:47  Salisbury                               1     On time
## 11:57  Great Malvern                           10A   On time
## 11:58  Plymouth                                11    On time
## 10:03  Bracknell                               BUS   On time
## 10:19  Bracknell                               BUS   On time
## 10:20  Swindon                                 BUS   On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 10:33  Bracknell                               BUS   On time
## 10:33  Guildford                               BUS   On time
## 10:49  Bracknell                               BUS   On time
## 11:03  Bracknell                               BUS   On time
## 11:07  Swindon                                 BUS   On time
## 11:18  Guildford                               BUS   On time
## 11:19  Bracknell                               BUS   On time
## 11:21  Heathrow Central Bus Stn                BUS   On time
## 11:33  Bracknell                               BUS   On time
## 11:49  Bracknell                               BUS   On time
## 11:50  Swindon                                 BUS   On time
## 12:02  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-09 10:03:31
## Time   To                                      Plat  Expected
## 10:02  London Paddington                       10A   On time
## 10:06  London Paddington                       15    On time
## 10:12  Hereford                                9B    On time
## 10:12  Salisbury                               7     On time
## 10:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 10:16  Bristol Temple Meads                    7     10:17
## 10:26  Didcot Parkway                          13    On time
## 10:27  Ealing Broadway                         14    On time
## 10:28  Penzance                                7     On time
## 10:30  London Paddington                       11    On time
## 10:33  Swansea                                 8     On time
## 10:38  Basingstoke                             2     On time
## 10:40  London Paddington                       10    On time
## 10:44  Newbury                                 1     On time
## 10:50  London Paddington                       11    12:03
## 10:57  Ealing Broadway                         14    On time
## 11:00  London Paddington                       10    On time
## 11:03  Exeter St Davids                        -     Cancelled
## 11:12  London Paddington                       15    On time
## 11:12  Salisbury                               1     On time
## 11:14  Great Malvern                           9B    On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 11:18  Bristol Temple Meads                    8     On time
## 11:26  Didcot Parkway                          12    On time
## 11:27  Ealing Broadway                         14    On time
## 11:28  Plymouth                                7     On time
## 11:30  London Paddington                       11    On time
## 11:33  Carmarthen                              8     On time
## 11:38  Basingstoke                             2     On time
## 11:40  London Paddington                       10    On time
## 11:44  Bedwyn                                  1     On time
## 11:50  London Paddington                       11    On time
## 11:52  Bournemouth                             7     On time
## 11:52  Ealing Broadway                         14    On time
## 11:59  London Paddington                       11    On time
## 12:01  London Paddington                       10A   On time
## 10:05  Swindon                                 BUS   On time
## 10:16  Bracknell                               BUS   On time
## 10:25  Swindon                                 BUS   On time
## 10:31  Bracknell                               BUS   On time
## 10:35  Guildford                               BUS   On time
## 10:46  Bracknell                               BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
## 11:01  Bracknell                               BUS   On time
## 11:05  Swindon                                 BUS   On time
## 11:08  Guildford                               BUS   On time
## 11:16  Bracknell                               BUS   On time
## 11:25  Swindon                                 BUS   On time
## 11:31  Bracknell                               BUS   On time
## 11:46  Bracknell                               BUS   On time
## 11:46  Guildford                               BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 12:01  Bracknell                               BUS   On time
```
