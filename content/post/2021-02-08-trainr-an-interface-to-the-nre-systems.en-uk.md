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

## Example (Last rendered on 2021-11-14 20:03)

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
## Reading (RDG) Station Board on 2021-11-14 20:03:30
## Time   From                                    Plat  Expected
## 19:50  London Paddington                       9     20:01
## 19:56  Hereford                                15    On time
## 19:58  Plymouth                                11    20:15
## 20:06  London Paddington                       9     On time
## 20:12  London Paddington                       8B    On time
## 20:13  Didcot Parkway                          13    On time
## 20:13  London Paddington                       14    On time
## 20:20  Newbury                                 1     On time
## 20:22  London Waterloo                         6     On time
## 20:23  London Paddington                       13    On time
## 20:32  London Paddington                       7     On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   8     20:50
## 20:40  Plymouth                                11    20:45
## 20:43  London Paddington                       14    On time
## 20:43  Swansea                                 10    21:12
## 20:50  London Paddington                       -     Cancelled
## 20:52  London Waterloo                         4     On time
## 20:56  Great Malvern                           15A   On time
## 20:58  Plymouth                                11    On time
## 21:06  London Paddington                       7     On time
## 21:07  Eastleigh                               8     On time
## 21:12  London Paddington                       7     On time
## 21:12  Taunton                                 10    On time
## 21:13  Didcot Parkway                          13    On time
## 21:15  London Paddington                       14    On time
## 21:19  Bedwyn                                  1     On time
## 21:22  London Waterloo                         5     On time
## 21:23  London Paddington                       12    On time
## 21:32  London Paddington                       7     On time
## 21:33  Basingstoke                             2     On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:43  London Paddington                       14    On time
## 21:43  Swansea                                 10    On time
## 21:47  London Paddington                       9     On time
## 21:56  London Waterloo                         4     On time
## 21:59  Great Malvern                           10A   On time
## 22:01  London Paddington                       9     On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 20:40  Guildford                               BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
## 21:08  Guildford                               BUS   On time
## 21:51  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-14 20:03:34
## Time   To                                      Plat  Expected
## 19:55  Bristol Temple Meads                    9     20:02
## 20:00  London Paddington                       11    20:16
## 20:05  London Paddington                       15    On time
## 20:09  Swansea                                 9     On time
## 20:14  Ealing Broadway                         13    On time
## 20:14  Great Malvern                           8B    On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:21  London Waterloo                         4     On time
## 20:22  Ealing Broadway                         14    On time
## 20:26  Didcot Parkway                          13    On time
## 20:33  Plymouth                                7     On time
## 20:38  Basingstoke                             2     On time
## 20:42  London Paddington                       11    20:46
## 20:42  Newbury                                 1     On time
## 20:46  London Paddington                       10    21:13
## 20:51  Ealing Broadway                         14    On time
## 20:51  London Waterloo                         6     On time
## 20:52  Eastleigh                               8     On time
## 20:55  Weston-super-Mare                       -     Cancelled
## 21:00  London Paddington                       11    On time
## 21:05  London Paddington                       15A   On time
## 21:09  Swansea                                 7     On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:13  London Paddington                       10    On time
## 21:14  Ealing Broadway                         13    On time
## 21:14  Worcester Shrub Hill                    7     On time
## 21:21  London Waterloo                         4     On time
## 21:25  Didcot Parkway                          12    On time
## 21:30  Ealing Broadway                         14    On time
## 21:33  Exeter St Davids                        7     On time
## 21:38  Basingstoke                             2     On time
## 21:44  Bedwyn                                  1     On time
## 21:45  London Paddington                       10    On time
## 21:48  Oxford                                  9     On time
## 21:51  London Waterloo                         5     On time
## 21:52  Eastleigh                               8     On time
## 22:00  Ealing Broadway                         14    On time
## 22:00  London Paddington                       10A   On time
## 22:02  Bristol Temple Meads                    9     On time
## 20:10  Guildford                               BUS   On time
## 20:35  Guildford                               BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 22:00  Guildford                               BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
```
