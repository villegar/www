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

## Example (Last rendered on 2023-03-12 16:03)

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
## Reading (RDG) Station Board on 2023-03-12 16:03:11
## Time   From                                    Plat  Expected
## 15:39  Manchester Piccadilly                   7     15:58
## 15:57  Great Malvern                           10A   16:01
## 16:07  London Paddington                       8     On time
## 16:08  Guildford                               6     On time
## 16:09  Bristol Temple Meads                    10    16:11
## 16:12  London Paddington                       9B    On time
## 16:13  Didcot Parkway                          14    16:17
## 16:13  London Paddington                       12B   On time
## 16:14  Exeter St Davids                        11    16:28
## 16:23  London Paddington                       9     16:32
## 16:25  Oxford                                  10    On time
## 16:28  London Paddington                       14    On time
## 16:31  London Waterloo                         4     On time
## 16:32  Basingstoke                             2     On time
## 16:32  Cheltenham Spa                          10A   On time
## 16:38  Guildford                               5     On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:40  Bristol Temple Meads                    11    On time
## 16:45  Swansea                                 10    On time
## 16:47  London Paddington                       9B    On time
## 16:47  Salisbury                               1     On time
## 16:53  London Paddington                       8     On time
## 16:57  Hereford                                10    On time
## 16:58  London Paddington                       14    On time
## 17:01  London Waterloo                         4     On time
## 17:06  Southampton Central                     8     On time
## 17:07  London Paddington                       7     On time
## 17:08  Guildford                               6     On time
## 17:09  Weston-super-Mare                       10    On time
## 17:13  Didcot Parkway                          14    On time
## 17:13  London Paddington                       9     On time
## 17:13  London Paddington                       12B   On time
## 17:23  London Paddington                       9     On time
## 17:25  Oxford                                  10    On time
## 17:28  London Paddington                       14    On time
## 17:28  Penzance                                11    On time
## 17:31  London Waterloo                         4     On time
## 17:32  Basingstoke                             2     On time
## 17:38  Guildford                               5     On time
## 17:39  Manchester Piccadilly                   8B    On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:44  Swansea                                 11    On time
## 17:47  London Paddington                       9     On time
## 17:53  London Paddington                       9     On time
## 17:56  London Paddington                       8     On time
## 17:57  Hereford                                10    On time
## 17:58  London Paddington                       14    On time
## 18:01  London Waterloo                         4     On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:06  Bedwyn                                  BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:39  Newbury                                 BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-12 16:03:18
## Time   To                                      Plat  Expected
## 15:52  Southampton Central                     7     Delayed
## 16:02  London Paddington                       10A   On time
## 16:03  Penzance                                9     On time
## 16:10  Swansea                                 8     On time
## 16:11  London Paddington                       10    16:12
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         14    16:18
## 16:14  Hereford                                9B    On time
## 16:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 16:16  London Paddington                       11    16:29
## 16:21  Guildford                               5     On time
## 16:23  Ealing Broadway                         15    On time
## 16:24  London Waterloo                         4     On time
## 16:25  Bristol Temple Meads                    9     16:33
## 16:25  Didcot Parkway                          12B   On time
## 16:26  London Paddington                       10    On time
## 16:34  London Paddington                       10A   On time
## 16:37  Basingstoke                             2     On time
## 16:41  Guildford                               6     On time
## 16:43  London Paddington                       11    On time
## 16:46  London Paddington                       10    On time
## 16:49  Oxford                                  9B    On time
## 16:53  Ealing Broadway                         15    On time
## 16:54  London Waterloo                         4     On time
## 16:55  Plymouth                                8     On time
##        via Bristol                             
## 17:00  London Paddington                       10    On time
## 17:03  Penzance                                9     On time
## 17:10  Swansea                                 7     On time
## 17:11  London Paddington                       10    On time
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         14    On time
## 17:14  Great Malvern                           9     On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:21  Guildford                               5     On time
## 17:23  Ealing Broadway                         15    On time
## 17:24  London Waterloo                         4     On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12B   On time
## 17:27  London Paddington                       10    On time
## 17:32  London Paddington                       11    On time
## 17:37  Basingstoke                             2     On time
## 17:41  Guildford                               6     On time
## 17:42  London Paddington                       10    On time
## 17:46  London Paddington                       11    On time
## 17:49  Oxford                                  9     On time
## 17:52  Southampton Central                     8B    On time
## 17:53  Ealing Broadway                         15    On time
## 17:54  London Waterloo                         4     On time
## 17:55  Weston-super-Mare                       9     On time
## 17:58  Cheltenham Spa                          8     On time
## 18:01  London Paddington                       10    On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:43  Newbury                                 BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:43  Bedwyn                                  BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
