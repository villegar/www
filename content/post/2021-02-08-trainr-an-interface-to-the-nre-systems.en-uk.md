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

## Example (Last rendered on 2022-11-27 16:03)

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
## Reading (RDG) Station Board on 2022-11-27 16:03:56
## Time   From                                    Plat  Expected
## 15:56  Hereford                                15    On time
## 15:58  Exeter St Davids                        11    16:05
## 16:03  Abbey Wood                              14    On time
## 16:06  London Paddington                       8     16:16
## 16:10  Didcot Parkway                          15A   On time
## 16:11  London Paddington                       12B   On time
## 16:12  Newbury                                 3     16:20
## 16:14  Bristol Temple Meads                    14    16:20
## 16:15  London Paddington                       12B   On time
## 16:23  London Paddington                       8     On time
## 16:25  London Waterloo                         4     16:28
## 16:25  Oxford                                  15A   On time
## 16:26  London Paddington                       7     On time
## 16:33  Abbey Wood                              14    On time
## 16:33  Basingstoke                             2     On time
## 16:33  Cheltenham Spa                          15A   On time
## 16:39  Manchester Piccadilly                   13    16:41
## 16:45  Swansea                                 15    16:55
## 16:47  London Paddington                       8B    On time
## 16:47  Salisbury                               1     On time
## 16:53  London Paddington                       8     On time
## 16:56  Great Malvern                           15A   On time
## 16:58  London Waterloo                         6     On time
## 16:58  Plymouth                                11    On time
## 17:00  London Paddington                       7     On time
## 17:03  Abbey Wood                              14    On time
## 17:05  Southampton Central                     7     On time
## 17:06  London Paddington                       8     On time
## 17:10  Didcot Parkway                          15A   On time
## 17:11  London Paddington                       8     On time
## 17:14  Weston-super-Mare                       12    On time
## 17:16  London Paddington                       8B    On time
## 17:21  Bedwyn                                  3     On time
## 17:24  London Paddington                       12    On time
## 17:25  London Waterloo                         4     On time
## 17:25  Oxford                                  15A   On time
## 17:27  London Paddington                       7     On time
## 17:33  Abbey Wood                              9     On time
## 17:33  Basingstoke                             2     On time
## 17:39  Manchester Piccadilly                   7     On time
## 17:39  Paignton                                11    On time
## 17:41  Bristol Temple Meads                    15    On time
## 17:45  Swansea                                 14    On time
## 17:47  London Paddington                       8     On time
## 17:53  London Paddington                       8     On time
## 17:56  Hereford                                15    On time
## 17:56  London Paddington                       7     On time
## 17:57  Plymouth                                11    On time
## 17:58  London Waterloo                         6     On time
## 16:04  Guildford                               BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:40  Guildford                               BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:18  Guildford                               BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-27 16:04:02
## Time   To                                      Plat  Expected
## 15:58  London Paddington                       11    16:06
## 16:02  London Paddington                       15    On time
## 16:08  Swansea                                 8     16:17
## 16:12  Hereford                                12B   On time
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         15A   On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:16  London Paddington                       14    16:22
## 16:21  London Waterloo                         6     On time
## 16:24  Abbey Wood                              14    On time
## 16:25  Bristol Temple Meads                    8     On time
## 16:26  London Paddington                       15A   On time
## 16:28  Didcot Parkway                          12B   On time
## 16:28  Plymouth                                7     On time
## 16:35  London Paddington                       15A   On time
## 16:38  Basingstoke                             2     On time
## 16:43  Newbury                                 3     On time
## 16:46  London Paddington                       15    16:56
## 16:49  Oxford                                  8B    On time
## 16:51  London Waterloo                         4     On time
## 16:54  Abbey Wood                              14    On time
## 16:55  Bristol Temple Meads                    8     On time
## 16:59  London Paddington                       11    On time
## 17:02  London Paddington                       15A   On time
## 17:02  Plymouth                                7     On time
## 17:08  Swansea                                 8     On time
## 17:12  Great Malvern                           8     On time
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15A   On time
## 17:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 17:16  London Paddington                       12    On time
## 17:21  London Waterloo                         6     On time
## 17:24  Abbey Wood                              14    On time
## 17:25  Bristol Temple Meads                    12    On time
## 17:26  London Paddington                       15A   On time
## 17:28  Didcot Parkway                          8B    On time
## 17:28  Plymouth                                7     On time
## 17:38  Basingstoke                             2     On time
## 17:40  London Paddington                       11    On time
## 17:43  Bedwyn                                  3     On time
## 17:45  London Paddington                       15    On time
## 17:49  London Paddington                       14    On time
## 17:49  Oxford                                  8     On time
## 17:51  London Waterloo                         4     On time
## 17:52  Southampton Central                     7     On time
## 17:54  Abbey Wood                              9     On time
## 17:55  Weston-super-Mare                       8     On time
## 17:58  Cheltenham Spa                          7     On time
## 17:59  London Paddington                       11    On time
## 18:02  London Paddington                       15    On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:45  Guildford                               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:23  Guildford                               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:56  Guildford                               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
