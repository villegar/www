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

## Example (Last rendered on 2023-03-26 14:03)

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
## Reading (RDG) Station Board on 2023-03-26 14:03:14
## Time   From                                    Plat  Expected
## 14:57  Penzance                                11    14:54
## 15:02  Didcot Parkway                          10A   On time
## 15:06  Bournemouth                             8     On time
## 15:08  Guildford                               5     On time
## 15:10  Weston-super-Mare                       11    15:14
## 15:12  London Paddington                       9     15:16
## 15:13  Didcot Parkway                          15A   On time
## 15:13  London Paddington                       12B   On time
## 15:18  Bedwyn                                  3     On time
## 15:19  London Paddington                       9B    15:22
## 15:21  London Paddington                       8     On time
## 15:28  Abbey Wood                              14    15:35
## 15:28  London Paddington                       7     On time
## 15:33  Basingstoke                             2     On time
## 15:35  Exeter St Davids                        11    On time
## 15:38  Guildford                               7A    On time
## 15:39  Didcot Parkway                          8     On time
## 15:46  London Paddington                       9     On time
## 15:46  Swansea                                 10    On time
## 15:47  Salisbury                               1     On time
## 15:58  Exeter St Davids                        11    On time
## 16:01  Abbey Wood                              14    On time
## 16:02  Didcot Parkway                          10A   On time
## 16:08  Guildford                               5     On time
## 16:10  Bristol Temple Meads                    11    On time
## 16:12  London Paddington                       9     On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15A   On time
## 16:13  London Paddington                       12B   On time
## 16:19  London Paddington                       9B    On time
## 16:21  London Paddington                       8     On time
## 16:28  Abbey Wood                              14    On time
## 16:28  London Paddington                       7     On time
## 16:32  Cheltenham Spa                          10A   On time
## 16:33  Basingstoke                             2     On time
## 16:38  Guildford                               7A    On time
## 16:39  Didcot Parkway                          13    On time
## 16:40  Bristol Temple Meads                    11    On time
## 16:46  London Paddington                       9     On time
## 16:46  Swansea                                 10    On time
## 16:47  Salisbury                               1     On time
## 16:57  London Paddington                       8     On time
## 16:57  Penzance                                11    On time
## 16:59  Abbey Wood                              14    On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:26  Staines                                 BUS   On time
## 15:27  Staines                                 BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 15:56  Staines                                 BUS   On time
## 15:57  Staines                                 -     Cancelled
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:26  Staines                                 BUS   On time
## 16:27  Staines                                 -     Cancelled
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:56  Staines                                 BUS   On time
## 16:57  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-26 14:03:18
## Time   To                                      Plat  Expected
## 15:03  London Paddington                       11    On time
## 15:10  London Paddington                       10A   On time
## 15:12  Gillingham (Dorset)                     1     On time
## 15:13  Swansea                                 9     15:17
## 15:14  Ealing Broadway                         15A   On time
## 15:15  Didcot Parkway                          8     On time
## 15:17  London Paddington                       11    On time
## 15:20  Didcot Parkway                          9B    15:23
## 15:22  Guildford                               7A    On time
## 15:24  Abbey Wood                              14    On time
## 15:25  Bristol Temple Meads                    8     On time
## 15:28  Didcot Parkway                          12B   On time
## 15:28  Plymouth                                7     On time
## 15:37  Basingstoke                             2     On time
## 15:41  Guildford                               5     On time
## 15:43  Bedwyn                                  3     On time
## 15:45  London Paddington                       11    On time
## 15:47  London Paddington                       10    On time
## 15:52  Bournemouth                             8     On time
## 15:54  Abbey Wood                              14    On time
## 15:55  Taunton                                 9     On time
## 16:03  London Paddington                       11    On time
## 16:10  London Paddington                       10A   On time
## 16:12  Salisbury                               1     On time
## 16:13  Swansea                                 9     On time
## 16:14  Ealing Broadway                         15A   On time
## 16:15  Didcot Parkway                          13    On time
## 16:17  London Paddington                       11    On time
## 16:20  Didcot Parkway                          9B    On time
## 16:22  Guildford                               7A    On time
## 16:24  Abbey Wood                              14    On time
## 16:25  Bristol Temple Meads                    8     On time
## 16:28  Didcot Parkway                          12B   On time
## 16:28  Penzance                                7     On time
## 16:34  London Paddington                       10A   On time
## 16:37  Basingstoke                             2     On time
## 16:41  Guildford                               5     On time
## 16:43  Newbury                                 3     On time
## 16:45  London Paddington                       11    On time
## 16:47  London Paddington                       10    On time
## 16:54  Abbey Wood                              14    On time
## 16:55  Plymouth                                9     On time
##        via Bristol                             
## 17:01  Plymouth                                8     On time
## 17:02  London Paddington                       11    On time
## 15:25  Staines                                 BUS   On time
## 15:27  Staines                                 -     Cancelled
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:55  Staines                                 BUS   On time
## 15:57  Staines                                 BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:25  Staines                                 -     Cancelled
## 16:27  Staines                                 BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:55  Staines                                 -     Cancelled
## 16:57  Staines                                 BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
