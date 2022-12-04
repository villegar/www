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

## Example (Last rendered on 2022-12-04 08:03)

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
## Reading (RDG) Station Board on 2022-12-04 08:03:56
## Time   From                                    Plat  Expected
## 08:08  London Paddington                       14    On time
## 08:18  London Paddington                       9     08:20
## 08:23  London Paddington                       7     On time
## 08:32  London Paddington                       7     On time
## 08:40  London Paddington                       14    On time
## 08:58  London Paddington                       7B    On time
## 09:03  London Paddington                       7B    On time
## 09:05  Didcot Parkway                          10    On time
## 09:09  London Paddington                       14    On time
## 09:10  Swindon                                 11    On time
## 09:13  London Paddington                       9     On time
## 09:15  Newbury                                 15    On time
## 09:16  London Paddington                       7     On time
## 09:23  London Paddington                       7     On time
## 09:24  Oxford                                  11A   On time
## 09:28  Bristol Parkway                         10    On time
## 09:33  Basingstoke                             2     On time
## 09:38  London Paddington                       14    On time
## 09:39  Bristol Temple Meads                    11    On time
## 09:42  London Paddington                       9B    On time
## 08:05  Ascot                                   BUS   On time
## 08:22  Guildford                               BUS   On time
## 08:25  Ascot                                   BUS   On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 08:40  Ascot                                   BUS   On time
## 08:55  Ascot                                   BUS   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:11  Ascot                                   BUS   On time
## 09:18  Basingstoke                             BUS   On time
## 09:25  Ascot                                   BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 09:40  Ascot                                   BUS   On time
## 09:55  Ascot                                   BUS   On time
## 09:56  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-04 08:03:59
## Time   To                                      Plat  Expected
## 08:11  London Paddington                       13    On time
## 08:19  Exeter St Davids                        9     08:21
## 08:25  Didcot Parkway                          7     On time
## 08:31  Ealing Broadway                         14    On time
## 08:39  Exeter St Davids                        7     On time
##        via Bristol                             
## 09:00  Swansea                                 7B    On time
## 09:01  Ealing Broadway                         14    On time
## 09:06  Ealing Broadway                         10    On time
## 09:10  Great Malvern                           7B    On time
## 09:11  London Paddington                       11    On time
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Plymouth                                7     On time
## 09:22  Didcot Parkway                          9     On time
## 09:30  London Paddington                       11A   On time
## 09:31  Ealing Broadway                         14    On time
## 09:35  Weston-super-Mare                       7     On time
## 09:38  Basingstoke                             2     On time
## 09:40  London Paddington                       10    On time
## 09:43  Bedwyn                                  12B   On time
## 09:48  London Paddington                       11    On time
## 09:48  Oxford                                  9B    On time
## 09:52  Bournemouth                             8     On time
## 10:01  Ealing Broadway                         14    On time
## 08:12  Ascot                                   BUS   On time
## 08:28  Ascot                                   BUS   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:42  Ascot                                   BUS   On time
## 08:45  Guildford                               BUS   On time
## 08:58  Ascot                                   BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
## 09:12  Ascot                                   BUS   On time
## 09:23  Guildford                               BUS   On time
## 09:28  Ascot                                   BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:42  Ascot                                   BUS   On time
## 09:56  Guildford                               BUS   On time
## 09:58  Ascot                                   BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
```
