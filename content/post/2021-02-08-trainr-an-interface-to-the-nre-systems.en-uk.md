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

## Example (Last rendered on 2023-04-09 06:03)

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
## Reading (RDG) Station Board on 2023-04-09 06:03:47
## Time   From                                    Plat  Expected
## 07:23  London Paddington                       9     On time
## 07:36  London Paddington                       10    On time
## 07:41  Gatwick Airport                         5     07:44
## 08:03  Weybridge                               4     On time
## 08:08  London Paddington                       14    On time
## 08:18  London Paddington                       9     On time
## 08:23  London Paddington                       12    On time
## 08:32  Virginia Water                          4     On time
## 08:37  London Paddington                       7     On time
## 08:40  London Paddington                       14    On time
## 08:54  Bristol Temple Meads                    11    On time
## 08:57  London Paddington                       7B    On time
## 09:02  Weybridge                               4     On time
## 07:25  Heathrow Central Bus Stn                BUS   On time
## 07:57  Heathrow Central Bus Stn                BUS   On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 08:34  Andover                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-09 06:03:51
## Time   To                                      Plat  Expected
## 07:10  London Paddington                       7     On time
## 07:24  Virginia Water                          6     On time
## 07:39  Redhill                                 8B    On time
## 07:54  London Paddington                       10    On time
## 07:54  Weybridge                               4     On time
## 08:12  London Paddington                       15    On time
## 08:19  Penzance                                9     On time
## 08:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 08:24  Didcot Parkway                          12    On time
## 08:24  London Paddington                       14    On time
## 08:24  Virginia Water                          4     On time
## 08:40  Penzance                                7     On time
##        via Bristol                             
## 08:40  Redhill                                 15    On time
## 08:53  Ealing Broadway                         14    On time
## 08:54  Weybridge                               4     On time
## 08:58  London Paddington                       11    On time
## 09:00  Swansea                                 7B    On time
## 07:30  Andover                                 BUS   On time
## 07:30  Heathrow Airport T3 (Bus)               BUS   On time
## 07:38  Basingstoke                             BUS   On time
## 08:00  Heathrow Airport T3 (Bus)               BUS   On time
## 08:06  Newbury                                 BUS   On time
## 08:30  Andover                                 BUS   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:34  Bedwyn                                  BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
```
