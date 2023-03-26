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

## Example (Last rendered on 2023-03-26 10:03)

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
## Reading (RDG) Station Board on 2023-03-26 10:03:23
## Time   From                                    Plat  Expected
## 10:58  London Paddington                       14    11:02
## 11:06  Bournemouth                             8     On time
## 11:08  Guildford                               5     On time
## 11:10  Bristol Temple Meads                    10    11:12
## 11:10  Didcot Parkway                          15A   On time
## 11:12  London Paddington                       9     11:14
## 11:15  London Paddington                       12B   On time
## 11:15  Swansea                                 11    11:18
## 11:19  Bedwyn                                  1     On time
## 11:19  London Paddington                       9B    On time
## 11:27  London Paddington                       7     On time
## 11:28  Abbey Wood                              14    On time
## 11:33  Basingstoke                             2     On time
## 11:34  Plymouth                                11    On time
## 11:38  Guildford                               7A    On time
## 11:39  Didcot Parkway                          8     On time
## 11:44  Swansea                                 10    On time
## 11:46  London Paddington                       9     On time
## 11:47  Salisbury                               1     On time
## 11:58  Plymouth                                11    On time
## 11:59  Abbey Wood                              14    On time
## 12:02  Didcot Parkway                          10A   On time
## 12:08  Guildford                               5     On time
## 12:10  Bristol Temple Meads                    11    On time
## 12:10  Didcot Parkway                          15A   On time
## 12:12  London Paddington                       9     On time
## 12:13  London Paddington                       12B   On time
## 12:19  London Paddington                       9B    On time
## 12:19  Newbury                                 1     On time
## 12:27  London Paddington                       7     On time
## 12:28  Abbey Wood                              14    On time
## 12:31  Cheltenham Spa                          10A   On time
## 12:32  Basingstoke                             2     On time
## 12:38  Guildford                               7A    On time
## 12:39  Didcot Parkway                          12    On time
## 12:44  Swansea                                 10    On time
## 12:46  London Paddington                       9     On time
## 12:47  Salisbury                               1     On time
## 12:53  Penzance                                11    On time
## 12:57  London Paddington                       8     On time
## 12:59  Abbey Wood                              14    On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:26  Staines                                 BUS   On time
## 11:27  Staines                                 BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 11:56  Staines                                 BUS   On time
## 11:57  Staines                                 BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:26  Staines                                 BUS   On time
## 12:27  Staines                                 -     Cancelled
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 12:56  Staines                                 BUS   On time
## 12:57  Staines                                 -     Cancelled
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-26 10:03:28
## Time   To                                      Plat  Expected
## 11:12  Salisbury                               1     On time
## 11:13  Swansea                                 9     11:15
## 11:14  Ealing Broadway                         15A   On time
## 11:15  Didcot Parkway                          8     On time
## 11:15  London Paddington                       10    On time
## 11:17  London Paddington                       11    11:19
## 11:21  Guildford                               7A    On time
## 11:22  Didcot Parkway                          9B    On time
## 11:24  Abbey Wood                              14    On time
## 11:28  Didcot Parkway                          12B   On time
## 11:28  Plymouth                                7     On time
## 11:37  Basingstoke                             2     On time
## 11:41  Guildford                               5     On time
## 11:43  Bedwyn                                  1     On time
## 11:45  London Paddington                       11    On time
## 11:47  London Paddington                       10    On time
## 11:52  Bournemouth                             8     On time
## 11:54  Abbey Wood                              14    On time
## 11:55  Bristol Temple Meads                    9     On time
## 12:03  London Paddington                       11    On time
## 12:10  London Paddington                       10A   On time
## 12:12  Salisbury                               1     On time
## 12:13  Swansea                                 9     On time
## 12:14  Ealing Broadway                         15A   On time
## 12:15  Didcot Parkway                          13    On time
## 12:17  London Paddington                       11    On time
## 12:21  Guildford                               7A    On time
## 12:22  Didcot Parkway                          9B    On time
## 12:24  Abbey Wood                              14    On time
## 12:28  Didcot Parkway                          12B   On time
## 12:28  Penzance                                7     On time
## 12:34  London Paddington                       10A   On time
## 12:37  Basingstoke                             2     On time
## 12:41  Guildford                               5     On time
## 12:43  Newbury                                 1     On time
## 12:47  London Paddington                       10    On time
## 12:54  Abbey Wood                              14    On time
## 12:55  Weston-super-Mare                       9     On time
## 12:57  London Paddington                       11    On time
## 13:01  Paignton                                8     On time
## 11:25  Staines                                 BUS   On time
## 11:27  Staines                                 BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:55  Staines                                 BUS   On time
## 11:57  Staines                                 BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:25  Staines                                 BUS   On time
## 12:27  Staines                                 BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:55  Staines                                 BUS   On time
## 12:57  Staines                                 BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
