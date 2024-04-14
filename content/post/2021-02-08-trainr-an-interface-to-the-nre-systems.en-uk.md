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

## Example (Last rendered on 2024-04-14 19:16)

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
## Reading (RDG) Station Board on 2024-04-14 19:16:42.372635
## Time   From                                    Plat  Expected
## 20:18  Newbury                                 1     20:20
## 20:22  Swindon                                 10A   On time
## 20:26  London Paddington                       7     On time
## 20:27  Guildford                               5     On time
## 20:31  Oxford                                  15    On time
## 20:32  Basingstoke                             2     On time
## 20:32  London Waterloo                         6     On time
## 20:35  Didcot Parkway                          12    On time
## 20:36  Abbey Wood                              14    20:41
## 20:39  Manchester Piccadilly                   7B    On time
## 20:41  Plymouth                                11    On time
## 20:45  London Paddington                       9     On time
## 20:48  Swansea                                 10    21:38
## 20:53  London Paddington                       8B    On time
## 20:57  London Paddington                       9     On time
## 20:58  Penzance                                11    21:09
## 21:00  Great Malvern                           10    On time
## 21:02  London Waterloo                         6     On time
## 21:04  London Paddington                       7     On time
## 21:06  Abbey Wood                              14    On time
## 21:06  Southampton Airport Parkway             8B    On time
## 21:07  London Paddington                       9     On time
## 21:10  Taunton                                 10    On time
## 21:19  Bedwyn                                  1     On time
## 21:24  Guildford                               5     On time
## 21:26  London Paddington                       7B    On time
## 21:32  Basingstoke                             2     On time
## 21:32  London Waterloo                         6     On time
## 21:35  Didcot Parkway                          12    On time
## 21:36  Abbey Wood                              13    On time
## 21:39  Manchester Piccadilly                   -     On time
## 21:44  Swansea                                 10    22:00
## 21:45  London Paddington                       14    On time
## 21:55  Great Malvern                           11    On time
## 21:56  London Paddington                       9     On time
## 21:59  London Paddington                       8     On time
## 22:02  London Paddington                       9     On time
## 22:02  London Waterloo                         6     On time
## 22:04  Plymouth                                11    On time
## 22:05  London Paddington                       8     On time
## 22:06  Abbey Wood                              14    On time
## 22:09  Weston-super-Mare                       10    On time
## 20:40  Heathrow Airport T3 (Bus)               BUS   On time
## 21:10  Heathrow Airport T3 (Bus)               BUS   On time
## 21:40  Heathrow Airport T3 (Bus)               BUS   On time
## 22:10  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-04-14 19:16:44.122836
## Time   To                                      Plat  Expected
## 20:23  London Paddington                       10A   On time
## 20:24  London Waterloo                         4     On time
## 20:26  Didcot Parkway                          13A   On time
## 20:28  Plymouth                                7     On time
## 20:32  Abbey Wood                              14    On time
## 20:35  Guildford                               5     On time
## 20:37  Basingstoke                             2     On time
## 20:43  Newbury                                 1     On time
## 20:44  London Paddington                       11    On time
## 20:45  Swindon                                 9     On time
## 20:52  Southampton Airport Parkway             7B    On time
## 20:54  London Waterloo                         6     On time
## 20:56  London Paddington                       10    21:39
## 20:56  Oxford                                  8B    On time
## 20:59  Weston-super-Mare                       9     On time
## 21:02  Abbey Wood                              14    On time
## 21:05  London Paddington                       11    21:10
## 21:07  London Paddington                       10    On time
## 21:09  Swansea                                 7     On time
## 21:12  Birmingham New Street                   8B    On time
##        via Coventry                            
## 21:13  London Paddington                       10    On time
## 21:14  Worcester Shrub Hill                    9     On time
## 21:16  Didcot Parkway                          12A   On time
## 21:24  London Waterloo                         6     On time
## 21:28  Exeter St Davids                        7B    On time
## 21:32  Abbey Wood                              14    On time
## 21:37  Basingstoke                             2     On time
## 21:40  Guildford                               5     On time
## 21:43  Bedwyn                                  1     On time
## 21:46  London Paddington                       10    22:01
## 21:52  Southampton Airport Parkway             -     On time
## 21:54  London Waterloo                         6     On time
## 21:57  London Paddington                       11    On time
## 21:57  Oxford                                  9     On time
## 22:01  Bristol Temple Meads                    8     On time
## 22:02  Ealing Broadway                         13    On time
## 22:06  London Paddington                       11    On time
## 22:09  Swansea                                 9     On time
## 22:14  London Paddington                       10    On time
## 22:14  Worcester Shrub Hill                    8     On time
## 20:30  Heathrow Airport T3 (Bus)               BUS   On time
## 21:05  Heathrow Airport T3 (Bus)               BUS   On time
## 22:05  Heathrow Airport T3 (Bus)               BUS   On time
```
