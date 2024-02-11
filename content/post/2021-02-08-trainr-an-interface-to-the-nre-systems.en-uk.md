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

## Example (Last rendered on 2024-02-11 11:08)

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
## Reading (RDG) Station Board on 2024-02-11 11:08:11.740558
## Time   From                                    Plat  Expected
## 11:06  Bournemouth                             8     On time
## 11:08  London Paddington                       9     On time
## 11:09  Bristol Temple Meads                    10    11:12
## 11:10  London Paddington                       14    On time
## 11:13  London Paddington                       9     On time
## 11:15  London Paddington                       12    On time
## 11:16  Swansea                                 10    On time
## 11:19  Bedwyn                                  1     On time
## 11:22  Oxford                                  10A   On time
## 11:26  London Paddington                       7     On time
## 11:30  London Paddington                       9     On time
## 11:33  Basingstoke                             2     On time
## 11:35  Didcot Parkway                          15    On time
## 11:35  Totnes                                  11A   On time
## 11:39  Manchester Piccadilly                   -     Cancelled
## 11:40  Custom House                            14    On time
## 11:44  Swansea                                 11    On time
## 11:45  London Paddington                       9B    On time
## 11:47  Salisbury                               2     On time
## 11:53  London Paddington                       9     On time
## 11:58  Great Malvern                           10A   On time
## 11:58  Totnes                                  11    On time
## 12:02  Swindon                                 10    On time
## 12:05  Bournemouth                             13B   On time
## 12:08  London Paddington                       9     On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:10  Abbey Wood                              14    On time
## 12:13  London Paddington                       8     On time
## 12:15  London Paddington                       12    On time
## 12:19  Newbury                                 1     On time
## 12:22  Oxford                                  10A   On time
## 12:24  London Paddington                       9     On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          10A   On time
## 12:32  Basingstoke                             2     On time
## 12:35  Didcot Parkway                          15    On time
## 12:40  Abbey Wood                              14    On time
## 12:40  Manchester Piccadilly                   7B    On time
## 12:44  Swansea                                 10    On time
## 12:45  London Paddington                       9     On time
## 12:47  Salisbury                               2     On time
## 12:53  London Paddington                       9     On time
## 12:53  Penzance                                11    On time
## 12:58  Great Malvern                           10A   On time
## 12:59  London Paddington                       7     On time
## 11:12  Ascot                                   BUS   On time
## 11:15  Heathrow Airport T3 (Bus)               BUS   On time
## 11:28  Ascot                                   BUS   On time
## 11:42  Ascot                                   BUS   On time
## 11:45  Heathrow Airport T3 (Bus)               BUS   On time
## 11:55  Gatwick Airport                         BUS   On time
## 11:58  Ascot                                   BUS   On time
## 12:05  Guildford                               BUS   On time
## 12:12  Ascot                                   BUS   On time
## 12:15  Heathrow Airport T3 (Bus)               BUS   On time
## 12:28  Ascot                                   BUS   On time
## 12:42  Ascot                                   BUS   On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
## 12:55  Gatwick Airport                         BUS   On time
## 12:58  Ascot                                   BUS   On time
## 13:05  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-02-11 11:08:15.752562
## Time   To                                      Plat  Expected
## 11:10  Swansea                                 9     On time
## 11:11  London Paddington                       10    11:13
## 11:12  Salisbury                               2     On time
## 11:14  Great Malvern                           9     On time
## 11:14  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:18  London Paddington                       10    On time
## 11:23  London Paddington                       10A   On time
## 11:25  Didcot Parkway                          12    On time
## 11:28  Plymouth                                7     On time
## 11:29  Abbey Wood                              14    On time
## 11:32  Swindon                                 9     On time
## 11:35  London Paddington                       11A   On time
## 11:37  Basingstoke                             2     On time
## 11:37  London Paddington                       15    On time
## 11:43  Bedwyn                                  1     On time
## 11:46  London Paddington                       11    On time
## 11:48  Oxford                                  9B    On time
## 11:52  Bournemouth                             -     Cancelled
## 11:55  Bristol Temple Meads                    9     On time
## 11:59  Abbey Wood                              14    On time
## 11:59  London Paddington                       10A   On time
## 12:01  London Paddington                       11    On time
## 12:03  London Paddington                       10    On time
## 12:10  Carmarthen                              9     On time
## 12:11  London Paddington                       10    On time
## 12:12  Salisbury                               2     On time
## 12:14  Hereford                                8     On time
## 12:14  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 12:23  London Paddington                       10A   On time
## 12:25  Didcot Parkway                          12    On time
## 12:26  Swindon                                 9     On time
## 12:28  Penzance                                7     On time
## 12:29  Abbey Wood                              14    On time
## 12:33  London Paddington                       10A   On time
## 12:37  Basingstoke                             2     On time
## 12:37  London Paddington                       15    On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       10    On time
## 12:48  Oxford                                  9     On time
## 12:52  Bournemouth                             7B    On time
## 12:53  London Paddington                       11    On time
## 12:55  Weston-super-Mare                       9     On time
## 12:59  Abbey Wood                              14    On time
## 13:00  London Paddington                       10A   On time
## 13:01  Paignton                                7     On time
## 11:15  Ascot                                   BUS   On time
## 11:20  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 11:20  Guildford                               BUS   On time
## 11:29  Ascot                                   BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:45  Ascot                                   BUS   On time
## 11:59  Ascot                                   BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:15  Ascot                                   BUS   On time
## 12:20  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 12:20  Guildford                               BUS   On time
## 12:29  Ascot                                   BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:45  Ascot                                   BUS   On time
## 12:59  Ascot                                   BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
