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

## Example (Last rendered on 2023-03-12 20:03)

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
## Reading (RDG) Station Board on 2023-03-12 20:03:33
## Time   From                                    Plat  Expected
## 19:49  Swansea                                 11    20:04
## 19:53  London Paddington                       9     20:00
## 19:55  Hereford                                11    19:59
## 20:07  London Paddington                       8     On time
## 20:08  Guildford                               15    On time
## 20:11  Bristol Temple Meads                    10    On time
## 20:12  London Paddington                       9B    20:14
## 20:13  Didcot Parkway                          13A   On time
## 20:14  Penzance                                11    On time
## 20:19  London Paddington                       12    On time
## 20:24  Oxford                                  10A   On time
## 20:27  London Paddington                       9     On time
## 20:28  London Paddington                       14    On time
## 20:31  London Waterloo                         6     On time
## 20:32  Basingstoke                             2     On time
## 20:38  Guildford                               5     On time
## 20:39  Manchester Piccadilly                   8     On time
## 20:47  London Paddington                       9     On time
## 20:49  Swansea                                 10    On time
## 20:53  London Paddington                       9     On time
## 20:58  Great Malvern                           10A   On time
## 20:58  London Paddington                       14    On time
## 21:01  London Waterloo                         4     On time
## 21:06  Southampton Central                     8     On time
## 21:07  London Paddington                       9     On time
## 21:08  Guildford                               15B   On time
## 21:11  Taunton                                 10    On time
## 21:12  London Paddington                       12    On time
## 21:12  London Paddington                       9     On time
## 21:13  Didcot Parkway                          13A   On time
## 21:26  London Paddington                       7     On time
## 21:27  Penzance                                11    On time
## 21:28  London Paddington                       14    On time
## 21:31  London Waterloo                         6     On time
## 21:32  Basingstoke                             2     On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:40  Guildford                               5     On time
## 21:42  London Paddington                       12    On time
## 21:49  Swansea                                 10    On time
## 21:53  Great Malvern                           11A   On time
## 21:53  London Paddington                       9     On time
## 21:58  London Paddington                       14    On time
## 22:01  London Waterloo                         6     On time
## 20:07  Bedwyn                                  BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:46  Newbury                                 BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-12 20:03:40
## Time   To                                      Plat  Expected
## 19:50  London Paddington                       11    20:05
## 19:55  Bristol Temple Meads                    9     20:01
## 20:01  London Paddington                       11    On time
## 20:09  Swansea                                 8     On time
## 20:13  Guildford                               5     On time
## 20:14  Ealing Broadway                         13A   On time
## 20:14  Great Malvern                           9B    20:15
## 20:14  London Paddington                       10    On time
## 20:15  Manchester Piccadilly                   14    On time
##        via Coventry & Stoke-on-Trent           
## 20:18  London Paddington                       11    On time
## 20:23  Ealing Broadway                         15A   On time
## 20:24  London Waterloo                         4     On time
## 20:25  Didcot Parkway                          12    On time
## 20:27  London Paddington                       10A   On time
## 20:28  Plymouth                                9     On time
## 20:37  Basingstoke                             2     On time
## 20:49  Oxford                                  9     On time
## 20:50  London Paddington                       10    On time
## 20:52  Southampton Central                     8     On time
## 20:53  Ealing Broadway                         15A   On time
## 20:54  London Waterloo                         6     On time
## 20:55  Weston-super-Mare                       9     On time
## 21:02  London Paddington                       10A   On time
## 21:09  Swansea                                 9     On time
## 21:11  London Paddington                       10    On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:13  Guildford                               5     On time
## 21:14  Didcot Parkway                          12    On time
## 21:14  Ealing Broadway                         13A   On time
## 21:15  Worcester Shrub Hill                    9     On time
## 21:24  Ealing Broadway                         15A   On time
## 21:24  London Waterloo                         4     On time
## 21:28  London Paddington                       11    On time
## 21:30  Exeter St Davids                        7     On time
## 21:37  Basingstoke                             2     On time
## 21:46  Oxford                                  12    On time
## 21:50  London Paddington                       10    On time
## 21:52  Southampton Central                     8     On time
## 21:54  Ealing Broadway                         15A   On time
## 21:54  London Waterloo                         6     On time
## 21:55  Bristol Temple Meads                    9     On time
## 21:55  London Paddington                       11A   On time
## 20:43  Newbury                                 BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:43  Bedwyn                                  BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
```
