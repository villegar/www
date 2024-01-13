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

## Example (Last rendered on 2024-01-13 15:04)

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
## Reading (RDG) Station Board on 2024-01-13 15:04:47.486617
## Time   From                                    Plat  Expected
## 14:52  Bristol Temple Meads                    11    15:13
## 14:58  London Paddington                       7B    15:03
## 15:01  Didcot Parkway                          15    On time
## 15:02  Penzance                                11    15:07
## 15:05  Bournemouth                             7B    On time
## 15:08  Newcastle                               3     On time
## 15:10  Abbey Wood                              14    On time
## 15:10  Bristol Temple Meads                    10    On time
## 15:11  London Paddington                       8B    On time
## 15:13  London Waterloo                         4     On time
## 15:14  London Paddington                       12    On time
## 15:15  London Paddington                       9B    On time
## 15:19  Basingstoke                             2     On time
## 15:23  London Paddington                       9     On time
## 15:24  Oxford                                  10    On time
## 15:26  London Paddington                       7     On time
## 15:27  Newbury                                 11A   On time
## 15:28  Gatwick Airport                         5     On time
## 15:31  Didcot Parkway                          15    On time
## 15:31  London Paddington                       8     On time
## 15:34  Gloucester                              10A   On time
## 15:38  London Paddington                       9     On time
## 15:40  Abbey Wood                              14    On time
## 15:40  Manchester Piccadilly                   7B    On time
## 15:41  Newbury                                 1     On time
## 15:43  London Paddington                       8B    On time
## 15:43  London Waterloo                         6     On time
## 15:44  London Paddington                       12    On time
## 15:46  Exeter St Davids                        11    On time
## 15:46  London Paddington                       9B    On time
## 15:48  Swansea                                 10    On time
## 15:51  Basingstoke                             2     On time
## 15:54  Bristol Temple Meads                    11    On time
## 15:57  Gatwick Airport                         4     On time
## 15:57  Hereford                                10    On time
## 15:57  Salisbury                               3     On time
## 16:00  Didcot Parkway                          15    On time
## 16:00  Plymouth                                11    On time
## 16:06  Bournemouth                             13B   On time
## 16:10  Abbey Wood                              14    On time
## 16:10  Bristol Temple Meads                    10    On time
## 16:11  London Paddington                       9     On time
## 16:13  London Waterloo                         5     On time
## 16:14  London Paddington                       12    On time
## 16:15  London Paddington                       8B    On time
## 16:19  Basingstoke                             2     On time
## 16:19  Cardiff Central                         10    On time
## 16:23  London Paddington                       9     On time
## 16:24  Oxford                                  10    On time
## 16:26  London Paddington                       7     On time
## 16:28  Gatwick Airport                         4     On time
## 16:28  Newbury                                 11A   On time
## 16:31  Didcot Parkway                          15    On time
## 16:31  London Paddington                       8B    On time
## 16:39  London Paddington                       8     On time
## 16:40  Abbey Wood                              14    On time
## 16:41  London Paddington                       9B    On time
## 16:41  Manchester Piccadilly                   7B    On time
## 16:41  Newbury                                 1     On time
## 16:43  London Waterloo                         6     On time
## 16:44  London Paddington                       12    On time
## 16:46  London Paddington                       9     On time
## 16:46  Swansea                                 10    On time
## 16:49  Basingstoke                             2     On time
## 16:52  Bristol Temple Meads                    -     Cancelled
## 16:55  London Paddington                       8B    On time
## 16:55  Salisbury                               3     On time
## 16:56  Great Malvern                           10    On time
## 16:57  Gatwick Airport                         5     On time
## 16:58  London Paddington                       7     On time
## 15:15  Heathrow Airport T3 (Bus)               BUS   On time
## 15:45  Heathrow Airport T3 (Bus)               BUS   On time
## 16:15  Heathrow Airport T3 (Bus)               BUS   On time
## 16:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-13 15:04:52.167914
## Time   To                                      Plat  Expected
## 14:54  London Paddington                       11    15:14
## 15:01  Plymouth                                7B    15:04
## 15:05  London Paddington                       11    15:08
## 15:09  Basingstoke                             2     On time
## 15:09  London Waterloo                         6     On time
## 15:12  London Paddington                       10    On time
## 15:12  Newbury                                 1     On time
## 15:13  Carmarthen                              8B    On time
## 15:13  London Paddington                       15    On time
## 15:15  Birmingham New Street                   7B    On time
##        via Coventry                            
## 15:15  Salisbury                               13B   On time
## 15:19  Great Malvern                           9B    On time
## 15:22  Didcot Parkway                          12    On time
## 15:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:25  Bristol Temple Meads                    9     On time
## 15:26  London Paddington                       10    On time
## 15:29  Abbey Wood                              14    On time
## 15:29  London Paddington                       11A   On time
## 15:29  Penzance                                7     On time
## 15:33  Newbury                                 8     On time
## 15:35  London Paddington                       10A   On time
## 15:37  Basingstoke                             2     On time
## 15:39  London Waterloo                         4     On time
## 15:40  Bristol Parkway                         9     On time
## 15:43  London Paddington                       15    On time
## 15:45  York                                    3     On time
##        via Doncaster                           
## 15:47  Bristol Temple Meads                    8B    On time
## 15:48  London Paddington                       11    On time
## 15:48  Oxford                                  9B    On time
## 15:50  London Paddington                       10    On time
## 15:52  Bournemouth                             7B    On time
## 15:53  Didcot Parkway                          12    On time
## 15:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:56  London Paddington                       11    On time
## 15:59  Abbey Wood                              14    On time
## 15:59  London Paddington                       10    On time
## 16:05  London Paddington                       11    On time
## 16:07  Basingstoke                             2     On time
## 16:09  London Waterloo                         6     On time
## 16:12  London Paddington                       10    On time
## 16:12  Newbury                                 1     On time
## 16:13  London Paddington                       15    On time
## 16:13  Swansea                                 9     On time
## 16:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 16:15  Salisbury                               3     On time
## 16:19  Great Malvern                           8B    On time
## 16:20  London Paddington                       10    On time
## 16:23  Didcot Parkway                          12    On time
## 16:24  Gatwick Airport                         4     On time
##        via Guildford                           
## 16:25  Bristol Temple Meads                    9     On time
## 16:27  London Paddington                       10    On time
## 16:29  Abbey Wood                              14    On time
## 16:29  Plymouth                                7     On time
## 16:31  London Paddington                       11A   On time
## 16:33  Newbury                                 8B    On time
## 16:37  Basingstoke                             2     On time
## 16:39  London Waterloo                         5     On time
## 16:43  Bristol Temple Meads                    8     On time
## 16:43  Cardiff Central                         9B    On time
## 16:43  London Paddington                       15    On time
## 16:49  Oxford                                  9     On time
## 16:50  London Paddington                       10    On time
## 16:52  Bournemouth                             7B    On time
## 16:53  Didcot Parkway                          12    On time
## 16:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 16:54  London Paddington                       -     Cancelled
## 16:58  Cheltenham Spa                          8B    On time
## 16:59  Abbey Wood                              14    On time
## 16:59  London Paddington                       10    On time
## 17:01  Paignton                                7     On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
