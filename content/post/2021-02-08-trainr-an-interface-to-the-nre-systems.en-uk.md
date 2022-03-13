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

## Example (Last rendered on 2022-03-13 10:05)

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
## Reading (RDG) Station Board on 2022-03-13 10:05:04
## Time   From                                    Plat  Expected
## 09:58  Didcot Parkway                          15    On time
## 09:59  Worcester Foregate Street               10A   10:06
## 10:03  Southampton Central                     7     09:53
## 10:06  London Waterloo                         4     10:02
## 10:08  Guildford                               6     10:13
## 10:08  London Paddington                       14    10:03
## 10:09  Weston-super-Mare                       10    10:11
## 10:10  London Paddington                       9     On time
## 10:13  London Paddington                       8     On time
## 10:14  Newbury                                 1     On time
## 10:22  Slough                                  13    On time
## 10:23  Cardiff Central                         11    On time
## 10:34  London Paddington                       9     On time
## 10:36  London Waterloo                         4     On time
## 10:39  Birmingham New Street                   13    On time
## 10:43  London Paddington                       14    On time
## 10:47  Exeter St Davids                        11    On time
## 10:53  Bristol Parkway                         10    On time
## 10:53  London Paddington                       9     On time
## 10:56  Southampton Central                     8     On time
## 10:57  Great Malvern                           11    On time
## 10:59  London Paddington                       7     On time
## 11:01  London Paddington                       9     On time
## 11:05  Bristol Temple Meads                    10    On time
## 11:07  London Waterloo                         4     On time
## 11:08  Guildford                               6     On time
## 11:08  London Paddington                       14    On time
## 11:10  Didcot Parkway                          15    On time
## 11:12  London Paddington                       9B    On time
## 11:14  Cardiff Central                         11    On time
## 11:19  Newbury                                 2     On time
## 11:22  Slough                                  12    On time
## 11:36  London Waterloo                         4     On time
## 11:38  London Paddington                       14    On time
## 11:39  Manchester Piccadilly                   13    On time
## 11:45  Cardiff Central                         11    On time
## 11:53  London Paddington                       9     On time
## 11:58  Great Malvern                           10A   On time
## 10:45  Heathrow Central Bus Stn                BUS   On time
## 10:48  Bramley (Hampshire)                     BUS   On time
## 11:00  Basingstoke                             BUS   On time
## 11:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-13 10:05:07
## Time   To                                      Plat  Expected
## 10:02  London Paddington                       10A   10:07
## 10:11  Hereford                                9     On time
## 10:14  Slough                                  15    On time
## 10:15  London Paddington                       10    On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Coventry & Wilmslow                 
## 10:16  Truro                                   8     On time
## 10:21  London Waterloo                         4     On time
## 10:25  Ealing Broadway                         14    On time
## 10:25  London Paddington                       11    On time
## 10:26  Didcot Parkway                          13    On time
## 10:38  Guildford                               6     On time
## 10:40  Bristol Parkway                         9     On time
## 10:44  Newbury                                 1     On time
## 10:46  Bournemouth                             13    On time
## 10:50  London Paddington                       11    On time
## 10:51  London Waterloo                         4     On time
## 10:55  Ealing Broadway                         14    On time
## 10:55  London Paddington                       10    On time
## 10:55  Weston-super-Mare                       9     On time
## 11:02  London Paddington                       11    On time
## 11:05  Plymouth                                7     On time
## 11:09  Cardiff Central                         9     On time
## 11:14  Great Malvern                           9B    On time
## 11:14  Slough                                  15    On time
## 11:15  London Paddington                       10    On time
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 11:20  London Paddington                       11    On time
## 11:21  London Waterloo                         4     On time
## 11:25  Ealing Broadway                         14    On time
## 11:26  Didcot Parkway                          12    On time
## 11:41  Guildford                               6     On time
## 11:44  Newbury                                 2     On time
## 11:50  London Paddington                       11    On time
## 11:51  London Waterloo                         4     On time
## 11:54  Bristol Temple Meads                    9     On time
## 11:55  Ealing Broadway                         14    On time
## 12:02  London Paddington                       10A   On time
## 10:38  Basingstoke                             BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
## 11:38  Bramley (Hampshire)                     BUS   On time
## 11:52  Basingstoke                             BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
```
