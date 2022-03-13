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

## Example (Last rendered on 2022-03-13 20:03)

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
## Reading (RDG) Station Board on 2022-03-13 20:03:58
## Time   From                                    Plat  Expected
## 20:06  London Waterloo                         4     20:21
## 20:07  London Paddington                       8     On time
## 20:10  Guildford                               5     On time
## 20:12  Bristol Temple Meads                    10A   20:14
## 20:12  London Paddington                       9B    On time
## 20:13  Didcot Parkway                          13    On time
## 20:13  London Paddington                       14    On time
## 20:18  London Paddington                       13    On time
## 20:20  Newbury                                 1     On time
## 20:24  Plymouth                                11    On time
## 20:27  London Paddington                       8     On time
## 20:29  Oxford                                  10A   On time
## 20:36  London Waterloo                         6     On time
## 20:39  Manchester Piccadilly                   8     On time
## 20:43  London Paddington                       14    On time
## 20:47  London Paddington                       13B   On time
## 20:49  Port Talbot Parkway                     10    On time
## 20:52  Plymouth                                11    On time
## 20:53  London Paddington                       -     Cancelled
## 20:56  Bournemouth                             7     On time
## 20:56  Great Malvern                           10A   20:58
## 21:06  London Waterloo                         4     On time
## 21:07  London Paddington                       9B    On time
## 21:09  Guildford                               15    On time
## 21:11  Taunton                                 10A   On time
## 21:12  London Paddington                       9     On time
## 21:13  Didcot Parkway                          13    On time
## 21:13  London Paddington                       14    On time
## 21:14  London Paddington                       12    On time
## 21:16  Truro                                   11    On time
## 21:19  Newbury                                 1     On time
## 21:26  London Paddington                       -     Cancelled
## 21:36  London Waterloo                         6     On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:42  London Paddington                       9     On time
## 21:43  London Paddington                       14    On time
## 21:48  Guildford                               5     On time
## 21:51  Port Talbot Parkway                     11    On time
## 21:53  London Paddington                       9     On time
## 21:57  Great Malvern                           10A   On time
## 20:18  Basingstoke                             BUS   On time
## 20:30  Heathrow Central Bus Stn                BUS   On time
## 21:00  Basingstoke                             BUS   On time
## 21:18  Bramley (Hampshire)                     BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-13 20:04:02
## Time   To                                      Plat  Expected
## 20:09  Port Talbot Parkway                     8     On time
## 20:13  Guildford                               6     On time
## 20:14  Ealing Broadway                         13    On time
## 20:14  Great Malvern                           9B    On time
## 20:14  London Paddington                       10A   20:15
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 20:21  London Waterloo                         4     20:24
## 20:22  Ealing Broadway                         14    On time
## 20:25  London Paddington                       11    On time
## 20:26  Didcot Parkway                          13    On time
## 20:29  Plymouth                                8     On time
## 20:31  London Paddington                       10A   On time
## 20:44  Newbury                                 1     On time
## 20:46  Southampton Central                     8     On time
## 20:49  Oxford                                  13B   On time
## 20:50  London Paddington                       10    On time
## 20:51  London Waterloo                         6     On time
## 20:52  Ealing Broadway                         14    On time
## 20:55  London Paddington                       11    On time
## 20:55  Weston-super-Mare                       -     Cancelled
## 21:01  London Paddington                       10A   On time
## 21:09  Port Talbot Parkway                     9B    On time
## 21:12  Birmingham New Street                   7     On time
##        via Coventry                            
## 21:13  Guildford                               5     On time
## 21:13  London Paddington                       10A   On time
## 21:14  Didcot Parkway                          12    On time
## 21:14  Ealing Broadway                         13    On time
## 21:15  Worcester Shrub Hill                    9     On time
## 21:20  London Paddington                       11    On time
## 21:21  London Waterloo                         4     On time
## 21:25  Ealing Broadway                         14    On time
## 21:28  Exeter St Davids                        -     Cancelled
## 21:44  Newbury                                 1     On time
## 21:46  Southampton Central                     8     On time
## 21:48  Oxford                                  9     On time
## 21:51  London Waterloo                         6     On time
## 21:55  Bristol Temple Meads                    9     On time
## 21:55  Ealing Broadway                         14    On time
## 21:55  London Paddington                       11    On time
## 21:59  London Paddington                       10A   On time
## 20:38  Bramley (Hampshire)                     BUS   On time
## 20:52  Basingstoke                             BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 21:38  Bramley (Hampshire)                     BUS   On time
## 21:52  Basingstoke                             BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
```
