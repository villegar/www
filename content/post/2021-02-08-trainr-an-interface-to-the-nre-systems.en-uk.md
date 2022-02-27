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

## Example (Last rendered on 2022-02-27 16:03)

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
## Reading (RDG) Station Board on 2022-02-27 16:03:45
## Time   From                                    Plat  Expected
## 15:43  London Paddington                       9B    16:03
## 15:57  Hereford                                10A   On time
## 15:58  Exeter St Davids                        11    16:02
## 16:02  Ascot                                   4     On time
## 16:07  London Paddington                       9     On time
## 16:09  Bristol Temple Meads                    10A   On time
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       9B    On time
## 16:13  London Paddington                       14    On time
## 16:15  London Paddington                       12    On time
## 16:15  Newbury                                 1     On time
## 16:23  London Paddington                       9B    On time
## 16:25  Oxford                                  10A   On time
## 16:26  London Paddington                       7     On time
## 16:32  Ascot                                   4     On time
## 16:32  Cheltenham Spa                          10A   On time
## 16:33  Basingstoke                             2     On time
## 16:39  Manchester Piccadilly                   13    16:58
## 16:43  London Paddington                       14    On time
## 16:46  London Paddington                       9B    On time
## 16:47  Swansea                                 10    On time
## 16:53  London Paddington                       9     On time
## 16:57  Great Malvern                           10A   On time
## 16:58  Exeter St Davids                        11    On time
## 17:00  London Paddington                       7     On time
## 17:02  Ascot                                   4     On time
## 17:07  London Paddington                       9     On time
## 17:07  Southampton Central                     8     On time
## 17:10  Weston-super-Mare                       10A   On time
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       9B    On time
## 17:13  London Paddington                       14    On time
## 17:15  London Paddington                       12    On time
## 17:20  Bedwyn                                  1     On time
## 17:23  London Paddington                       9     On time
## 17:25  Oxford                                  10A   On time
## 17:26  London Paddington                       7     On time
## 17:32  Ascot                                   4     On time
## 17:33  Basingstoke                             2     On time
## 17:37  Exeter St Davids                        11    On time
## 17:39  Manchester Piccadilly                   8B    On time
## 17:40  Bristol Temple Meads                    10A   On time
## 17:43  London Paddington                       14    On time
## 17:45  London Paddington                       9     On time
## 17:45  Swansea                                 11    On time
## 17:53  London Paddington                       9     On time
## 17:56  London Paddington                       8     On time
## 17:57  Exeter St Davids                        11    On time
## 17:57  Hereford                                10    On time
## 18:02  Ascot                                   4     On time
## 16:02  Guildford                               BUS   On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 16:45  Guildford                               BUS   On time
## 17:18  Guildford                               BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
## 18:02  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-27 16:03:48
## Time   To                                      Plat  Expected
## 15:48  Oxford                                  9B    16:04
## 15:58  London Paddington                       11    16:03
## 16:02  London Paddington                       10A   On time
## 16:09  Swansea                                 9     On time
## 16:11  London Paddington                       10A   On time
## 16:14  Ealing Broadway                         15    On time
## 16:15  Hereford                                9B    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 16:19  Ascot                                   4     On time
## 16:22  Ealing Broadway                         14    On time
## 16:24  Bristol Temple Meads                    9B    On time
## 16:25  Didcot Parkway                          12    On time
## 16:25  London Paddington                       10A   On time
## 16:28  Exeter St Davids                        7     On time
## 16:34  London Paddington                       10A   On time
## 16:38  Basingstoke                             2     On time
## 16:44  Newbury                                 1     On time
## 16:47  Oxford                                  9B    On time
## 16:49  Ascot                                   4     On time
## 16:50  London Paddington                       10    On time
## 16:52  Ealing Broadway                         14    On time
## 16:55  Bristol Temple Meads                    9     On time
## 16:59  London Paddington                       11    On time
## 17:01  London Paddington                       10A   On time
## 17:03  Exeter St Davids                        7     On time
## 17:09  Swansea                                 9     On time
## 17:12  London Paddington                       10A   On time
## 17:14  Ealing Broadway                         15    On time
## 17:14  Great Malvern                           9B    On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 17:19  Ascot                                   4     On time
## 17:22  Ealing Broadway                         14    On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12    On time
## 17:25  London Paddington                       10A   On time
## 17:28  Exeter St Davids                        7     On time
## 17:38  Basingstoke                             2     On time
## 17:40  London Paddington                       11    On time
## 17:44  Bedwyn                                  1     On time
## 17:45  London Paddington                       10A   On time
## 17:48  Oxford                                  9     On time
## 17:49  Ascot                                   4     On time
## 17:50  London Paddington                       11    On time
## 17:52  Ealing Broadway                         14    On time
## 17:52  Southampton Central                     8B    On time
## 17:55  Weston-super-Mare                       9     On time
## 17:58  Cheltenham Spa                          8     On time
## 17:59  London Paddington                       11    On time
## 18:01  London Paddington                       10    On time
## 16:35  Guildford                               BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 17:08  Guildford                               BUS   On time
## 17:46  Guildford                               BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
