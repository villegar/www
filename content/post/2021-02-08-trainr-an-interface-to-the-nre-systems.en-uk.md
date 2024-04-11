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

## Example (Last rendered on 2024-04-11 17:06)

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
## Reading (RDG) Station Board on 2024-04-11 17:06:52.166368
## Time   From                                    Plat  Expected
## 17:55  London Paddington                       8B    18:04
## 17:57  Hereford                                10    18:02
## 17:57  Plymouth                                11    18:05
## 18:03  Didcot Parkway                          14A   On time
## 18:07  Bournemouth                             7B    On time
## 18:10  Bristol Temple Meads                    10    On time
## 18:11  London Paddington                       9     On time
## 18:12  Abbey Wood                              14    On time
## 18:14  London Waterloo                         6     18:16
## 18:17  Cardiff Central                         11    18:19
## 18:20  Basingstoke                             2     On time
## 18:21  London Paddington                       9     18:25
## 18:23  Oxford                                  10A   On time
## 18:24  London Paddington                       8     On time
## 18:24  London Paddington                       12B   On time
## 18:25  Newbury                                 11A   On time
## 18:27  London Paddington                       7     On time
## 18:30  Gatwick Airport                         4     On time
## 18:31  Didcot Parkway                          14A   On time
## 18:34  Abbey Wood                              13    On time
## 18:34  Cheltenham Spa                          11A   On time
## 18:34  London Paddington                       7     On time
## 18:35  Newbury                                 1     On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:40  Newbury                                 11A   On time
## 18:41  Manchester Piccadilly                   7     On time
## 18:42  Abbey Wood                              14    On time
## 18:42  London Paddington                       9     On time
## 18:44  London Waterloo                         5     On time
## 18:48  London Paddington                       9B    On time
## 18:48  Swansea                                 10    On time
## 18:49  Basingstoke                             3     On time
## 18:54  London Paddington                       12B   On time
## 18:57  London Paddington                       8     On time
## 18:57  Penzance                                11    On time
## 18:58  Great Malvern                           10A   On time
## 18:59  London Paddington                       7     On time
## 19:04  Abbey Wood                              13    On time
## 19:04  Basingstoke                             2     On time
## 19:04  Gatwick Airport                         4     On time
## 19:05  Didcot Parkway                          15A   On time
## 19:08  Bournemouth                             8B    On time
## 19:09  Weston-super-Mare                       10    On time
## 19:11  London Paddington                       9     On time
## 19:14  Abbey Wood                              14    On time
## 19:15  Newbury                                 1     On time
## 19:16  Cardiff Central                         10    On time
## 19:17  London Waterloo                         6     On time
## 19:21  London Paddington                       9     On time
## 19:23  London Paddington                       12B   On time
## 19:23  Worcester Foregate Street               10A   On time
## 19:25  London Paddington                       8     On time
## 19:27  Didcot Parkway                          15A   On time
## 19:28  London Paddington                       7     On time
## 19:30  Gatwick Airport                         4     On time
## 19:31  Cheltenham Spa                          11A   On time
## 19:34  Abbey Wood                              13    On time
## 19:35  Basingstoke                             2     On time
## 19:35  London Paddington                       7B    On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:41  Abbey Wood                              14    On time
## 19:41  London Paddington                       8     On time
## 19:41  Manchester Piccadilly                   7B    On time
## 19:44  London Waterloo                         5     On time
## 19:46  Carmarthen                              10A   On time
## 19:47  Salisbury                               3     On time
## 19:48  London Paddington                       8B    On time
## 19:53  London Paddington                       9     On time
## 19:54  London Paddington                       13B   On time
## 19:54  Plymouth                                11    On time
## 19:55  Worcester Foregate Street               10A   On time
## 19:56  London Paddington                       8B    On time
## 19:57  Gatwick Airport                         4     On time
## 20:00  Basingstoke                             1     On time
## 20:04  Newbury                                 2     On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-04-11 17:06:54.841876
## Time   To                                      Plat  Expected
## 17:58  Cheltenham Spa                          8B    18:05
## 17:58  London Paddington                       11    18:06
## 18:00  London Paddington                       10    18:06
## 18:06  Newbury                                 12A   On time
## 18:08  London Paddington                       14A   On time
## 18:09  London Waterloo                         4     On time
## 18:12  London Paddington                       10    On time
## 18:13  Carmarthen                              9     On time
## 18:15  Abbey Wood                              13    On time
## 18:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 18:19  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:20  London Paddington                       11    On time
## 18:23  Worcester Foregate Street               9     18:26
## 18:25  London Paddington                       10A   On time
## 18:26  Bristol Temple Meads                    8     On time
## 18:27  London Paddington                       11A   On time
## 18:28  Abbey Wood                              14    On time
## 18:29  Penzance                                7     On time
## 18:31  Didcot Parkway                          12B   On time
## 18:32  Basingstoke                             2     On time
## 18:33  London Paddington                       14A   On time
## 18:36  London Paddington                       11A   On time
## 18:37  Frome                                   7     On time
## 18:39  London Waterloo                         6     On time
## 18:43  London Paddington                       10    On time
## 18:43  Swansea                                 9     On time
## 18:45  Abbey Wood                              13    On time
## 18:45  London Paddington                       11A   On time
## 18:49  London Paddington                       10    On time
## 18:50  Banbury                                 9B    On time
## 18:52  Bournemouth                             7     On time
## 18:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 18:55  Weston-super-Mare                       9B    On time
## 18:58  London Paddington                       11    On time
## 18:59  Abbey Wood                              14    On time
## 18:59  Cheltenham Spa                          8     On time
## 19:00  Didcot Parkway                          12B   On time
## 19:01  Plymouth                                7     On time
## 19:03  London Paddington                       10A   On time
## 19:05  Basingstoke                             3     On time
## 19:09  London Waterloo                         5     On time
## 19:10  Newbury                                 1     On time
## 19:12  London Paddington                       15A   On time
## 19:13  London Paddington                       10    On time
## 19:13  Swansea                                 9     On time
## 19:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       10    On time
## 19:23  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:23  Great Malvern                           9     On time
## 19:25  Basingstoke                             2     On time
## 19:26  London Paddington                       10A   On time
## 19:27  Bristol Temple Meads                    8     On time
## 19:28  Didcot Parkway                          12B   On time
## 19:30  Abbey Wood                              14    On time
## 19:31  Plymouth                                7     On time
## 19:33  London Paddington                       11A   On time
## 19:37  Bedwyn                                  7B    On time
## 19:39  London Waterloo                         6     On time
## 19:41  London Paddington                       10    On time
## 19:42  London Paddington                       15A   On time
## 19:42  Newbury                                 1     On time
## 19:43  Swansea                                 8     On time
## 19:49  London Paddington                       10A   On time
## 19:49  Oxford                                  8B    On time
## 19:50  Bournemouth                             7B    On time
## 19:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:55  London Paddington                       11    On time
## 19:55  Weston-super-Mare                       9     On time
## 19:57  Basingstoke                             2     On time
## 19:57  Didcot Parkway                          13B   On time
## 19:58  Worcester Shrub Hill                    8B    On time
##        via Gloucester                          
## 20:00  Abbey Wood                              14    On time
## 20:00  London Paddington                       10A   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
