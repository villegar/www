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

## Example (Last rendered on 2024-03-30 17:06)

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
## Reading (RDG) Station Board on 2024-03-30 17:06:07.108016
## Time   From                                    Plat  Expected
## 16:59  Penzance                                11    17:33
## 17:01  Didcot Parkway                          15A   On time
## 17:06  Southampton Central                     13B   17:25
## 17:10  Bristol Temple Meads                    10    17:17
## 17:11  London Paddington                       14    On time
## 17:11  London Paddington                       9     On time
## 17:11  London Waterloo                         4     On time
## 17:14  London Paddington                       12B   On time
## 17:15  London Paddington                       8     17:20
## 17:19  Basingstoke                             2     On time
## 17:23  London Paddington                       9     On time
## 17:24  Oxford                                  10A   On time
## 17:26  London Paddington                       7     17:28
## 17:28  Gatwick Airport                         5     On time
## 17:28  Newbury                                 11A   On time
## 17:30  London Paddington                       8B    On time
## 17:31  Didcot Parkway                          15A   On time
## 17:34  Cheltenham Spa                          10A   On time
## 17:40  London Paddington                       14    On time
## 17:41  London Paddington                       9     On time
## 17:41  Manchester Piccadilly                   7     On time
## 17:41  Newbury                                 1     On time
## 17:41  Weston-super-Mare                       10    On time
## 17:43  London Waterloo                         6     On time
## 17:44  Paignton                                11    On time
## 17:45  London Paddington                       12B   On time
## 17:45  London Paddington                       8     On time
## 17:48  Swansea                                 10    On time
## 17:49  Basingstoke                             2     On time
## 17:53  London Paddington                       9     On time
## 17:57  Gatwick Airport                         4     On time
## 17:58  Hereford                                10    On time
## 17:58  Plymouth                                11    On time
## 18:01  Didcot Parkway                          15A   On time
## 18:08  Southampton Central                     7     On time
## 18:10  Bristol Temple Meads                    10    On time
## 18:11  London Paddington                       14    On time
## 18:11  London Paddington                       9     On time
## 18:11  London Waterloo                         5     On time
## 18:14  London Paddington                       13B   On time
## 18:16  London Paddington                       9     On time
## 18:19  Basingstoke                             2     On time
## 18:21  Bristol Parkway                         11    On time
## 18:23  London Paddington                       9     On time
## 18:24  Oxford                                  10A   On time
## 18:26  London Paddington                       7     On time
## 18:28  Gatwick Airport                         4     On time
## 18:29  Newbury                                 11A   On time
## 18:31  Didcot Parkway                          15A   On time
## 18:31  London Paddington                       8B    On time
## 18:34  Cheltenham Spa                          10A   On time
## 18:40  London Paddington                       14    On time
## 18:40  Weston-super-Mare                       11    On time
## 18:41  London Paddington                       8     On time
## 18:41  Manchester Piccadilly                   7B    On time
## 18:41  Newbury                                 1     On time
## 18:43  London Paddington                       9B    On time
## 18:43  London Waterloo                         6     On time
## 18:44  London Paddington                       12B   On time
## 18:46  Carmarthen                              10A   On time
## 18:49  Basingstoke                             2     On time
## 18:53  London Paddington                       8     On time
## 18:57  Gatwick Airport                         5     On time
## 18:58  Great Malvern                           10A   On time
## 18:58  London Paddington                       9     On time
## 19:01  Penzance                                11    On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-30 17:06:09.658702
## Time   To                                      Plat  Expected
## 17:05  London Paddington                       11    17:34
## 17:07  Basingstoke                             2     On time
## 17:09  London Waterloo                         6     On time
## 17:12  London Paddington                       10    17:18
## 17:12  Newbury                                 1     On time
## 17:13  London Paddington                       15A   On time
## 17:13  Swansea                                 9     On time
## 17:15  Manchester Piccadilly                   13B   17:26
##        via Coventry & Stoke-on-Trent           
## 17:19  Hereford                                8     17:21
## 17:23  Didcot Parkway                          12B   On time
## 17:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:25  Bristol Temple Meads                    9     On time
## 17:28  London Paddington                       10A   On time
## 17:29  Ealing Broadway                         14    On time
## 17:29  Penzance                                7     On time
## 17:31  London Paddington                       11A   On time
## 17:33  Newbury                                 8B    On time
## 17:35  London Paddington                       10A   On time
## 17:37  Basingstoke                             2     On time
## 17:39  London Waterloo                         4     On time
## 17:42  London Paddington                       10    On time
## 17:43  Carmarthen                              9     On time
## 17:43  London Paddington                       15A   On time
## 17:46  London Paddington                       11    On time
## 17:48  Oxford                                  8     On time
## 17:50  London Paddington                       10    On time
## 17:52  Southampton Central                     7     On time
## 17:53  Didcot Parkway                          12B   On time
## 17:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:55  Weston-super-Mare                       9     On time
## 17:58  Cheltenham Spa                          8B    On time
## 17:59  Ealing Broadway                         14    On time
## 18:00  London Paddington                       10    On time
## 18:05  London Paddington                       11    On time
## 18:07  Basingstoke                             2     On time
## 18:09  London Waterloo                         6     On time
## 18:12  London Paddington                       10    On time
## 18:12  Newbury                                 1     On time
## 18:13  London Paddington                       15A   On time
## 18:13  Swansea                                 9     On time
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 18:19  Worcester Foregate Street               9     On time
## 18:22  London Paddington                       11    On time
## 18:23  Didcot Parkway                          13B   On time
## 18:24  Gatwick Airport                         4     On time
##        via Guildford                           
## 18:25  Bristol Temple Meads                    9     On time
## 18:28  London Paddington                       10A   On time
## 18:29  Ealing Broadway                         14    On time
## 18:29  Penzance                                7     On time
## 18:32  London Paddington                       11A   On time
## 18:33  Newbury                                 8B    On time
## 18:35  London Paddington                       10A   On time
## 18:37  Basingstoke                             2     On time
## 18:39  London Waterloo                         5     On time
## 18:42  London Paddington                       11    On time
## 18:43  London Paddington                       15A   On time
## 18:43  Swansea                                 8     On time
## 18:47  Oxford                                  9B    On time
## 18:49  London Paddington                       10A   On time
## 18:50  Didcot Parkway                          12B   On time
## 18:52  Southampton Central                     7B    On time
## 18:53  Cheltenham Spa                          9B    On time
## 18:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 18:56  Taunton                                 8     On time
## 18:59  Ealing Broadway                         14    On time
## 19:00  London Paddington                       10A   On time
## 19:00  Swindon                                 9     On time
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       11    On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
