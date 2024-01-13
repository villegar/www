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

## Example (Last rendered on 2024-01-13 07:03)

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
## Reading (RDG) Station Board on 2024-01-13 07:03:59.650217
## Time   From                                    Plat  Expected
## 06:59  Bristol Temple Meads                    11    On time
## 07:04  Didcot Parkway                          15    On time
## 07:06  Southampton Central                     13B   On time
## 07:10  Bristol Temple Meads                    10    On time
## 07:10  London Paddington                       14    On time
## 07:11  London Paddington                       9     On time
## 07:11  London Waterloo                         4     On time
## 07:14  London Paddington                       12    On time
## 07:15  London Paddington                       8B    On time
## 07:19  Basingstoke                             2     On time
## 07:22  Newbury                                 11    On time
## 07:23  London Paddington                       9     On time
## 07:24  Oxford                                  10A   On time
## 07:31  London Paddington                       7     On time
## 07:32  Didcot Parkway                          15    On time
## 07:33  Swindon                                 11    On time
## 07:38  Newbury                                 1     On time
## 07:39  London Paddington                       8     On time
## 07:40  Abbey Wood                              14    On time
## 07:42  Birmingham New Street                   7B    On time
## 07:43  Virginia Water                          5     On time
## 07:44  London Paddington                       12    On time
## 07:45  London Paddington                       9B    On time
## 07:45  Swansea                                 11    07:48
## 07:49  Bristol Temple Meads                    10    On time
## 07:49  Gatwick Airport                         4     On time
## 07:55  London Paddington                       8     On time
## 07:56  Basingstoke                             2     On time
## 07:57  Great Malvern                           10    On time
## 07:58  Didcot Parkway                          15    On time
## 08:00  Salisbury                               3     On time
## 08:07  Bournemouth                             13B   On time
## 08:09  Weston-super-Mare                       11    On time
## 08:11  Abbey Wood                              14    On time
## 08:11  London Paddington                       9B    On time
## 08:13  London Waterloo                         4     On time
## 08:15  London Paddington                       8B    On time
## 08:16  Swansea                                 10    On time
## 08:19  London Paddington                       12    On time
## 08:20  Basingstoke                             2     On time
## 08:23  London Paddington                       9     On time
## 08:24  Oxford                                  10A   On time
## 08:26  London Paddington                       7     On time
## 08:28  Gatwick Airport                         5     On time
## 08:30  Newbury                                 11    On time
## 08:31  London Paddington                       8     On time
## 08:32  Cheltenham Spa                          10    On time
## 08:32  Didcot Parkway                          15    On time
## 08:38  London Paddington                       9     On time
## 08:40  Abbey Wood                              14    On time
## 08:41  London Paddington                       7     On time
## 08:41  Manchester Piccadilly                   8B    On time
## 08:42  Newbury                                 1     On time
## 08:43  London Waterloo                         6     On time
## 08:44  London Paddington                       9     On time
## 08:44  London Paddington                       12    On time
## 08:46  Swansea                                 10    On time
## 08:49  Basingstoke                             2     On time
## 08:55  London Paddington                       8     On time
## 08:56  Bristol Temple Meads                    11    On time
## 08:57  Gatwick Airport                         5     On time
## 08:58  Hereford                                10    On time
## 08:59  Honiton                                 3     On time
## 08:59  London Paddington                       7     On time
## 07:05  Heathrow Airport T3 (Bus)               BUS   On time
## 07:45  Heathrow Airport T3 (Bus)               BUS   On time
## 08:15  Heathrow Airport T3 (Bus)               BUS   On time
## 08:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-13 07:04:01.948462
## Time   To                                      Plat  Expected
## 07:01  London Paddington                       11    On time
## 07:04  Yeovil Junction                         3     On time
## 07:07  Basingstoke                             2     On time
## 07:09  London Waterloo                         6     On time
## 07:12  London Paddington                       10    On time
## 07:12  Newbury                                 7B    On time
## 07:13  Carmarthen                              9     On time
## 07:13  London Paddington                       15    On time
## 07:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 07:19  Great Malvern                           8B    On time
## 07:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 07:24  London Paddington                       11    On time
## 07:25  Bristol Temple Meads                    9     On time
## 07:26  Didcot Parkway                          12    On time
## 07:28  London Paddington                       10A   On time
## 07:29  Abbey Wood                              14    On time
## 07:32  Basingstoke                             2     On time
## 07:34  London Paddington                       11    On time
## 07:35  Newbury                                 7     On time
## 07:39  London Waterloo                         4     On time
## 07:42  Weston-super-Mare                       8     On time
## 07:43  London Paddington                       15    On time
## 07:47  Oxford                                  9B    On time
## 07:48  London Paddington                       11    07:48
## 07:51  London Paddington                       10    On time
## 07:52  Didcot Parkway                          12    On time
## 07:53  Bournemouth                             7B    On time
## 07:54  Gatwick Airport                         15A   On time
##        via Guildford                           
## 07:58  Cheltenham Spa                          8     On time
## 07:59  Abbey Wood                              14    On time
## 07:59  London Paddington                       10    On time
## 08:02  Newbury                                 1     On time
## 08:06  Gatwick Airport                         4     On time
##        via Guildford                           
## 08:07  Basingstoke                             2     On time
## 08:09  London Waterloo                         5     On time
## 08:12  London Paddington                       11    On time
## 08:13  London Paddington                       15    On time
## 08:13  Swansea                                 9B    On time
## 08:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 08:17  Salisbury                               3     On time
## 08:19  Great Malvern                           8B    On time
## 08:20  London Paddington                       10    On time
## 08:23  Didcot Parkway                          12    On time
## 08:25  Bristol Temple Meads                    9     On time
## 08:28  London Paddington                       10A   On time
## 08:29  Abbey Wood                              14    On time
## 08:29  Penzance                                7     On time
## 08:31  London Paddington                       11    On time
## 08:32  Newbury                                 8     On time
## 08:35  London Paddington                       10    On time
## 08:37  Basingstoke                             2     On time
## 08:39  London Waterloo                         4     On time
## 08:40  Bristol Parkway                         9     On time
## 08:43  London Paddington                       15    On time
## 08:44  Taunton                                 7     On time
## 08:47  Oxford                                  9     On time
## 08:50  Didcot Parkway                          12    On time
## 08:50  London Paddington                       10    On time
## 08:52  Bournemouth                             8B    On time
## 08:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 08:57  London Paddington                       11    On time
## 08:58  Cheltenham Spa                          8     On time
## 08:59  Abbey Wood                              14    On time
## 09:00  London Paddington                       10    On time
## 09:02  Exeter St Davids                        7     On time
## 07:25  Heathrow Airport T3 (Bus)               BUS   On time
## 07:55  Heathrow Airport T3 (Bus)               BUS   On time
## 08:25  Heathrow Airport T3 (Bus)               BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
```
