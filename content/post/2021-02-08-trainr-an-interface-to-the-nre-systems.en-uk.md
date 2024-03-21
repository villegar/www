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

## Example (Last rendered on 2024-03-21 05:06)

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
## Reading (RDG) Station Board on 2024-03-21 05:06:25.274349
## Time   From                                    Plat  Expected
## 05:34  Didcot Parkway                          15    On time
## 05:39  London Paddington                       9     On time
## 05:46  Oxford                                  10A   On time
## 05:47  London Paddington                       9B    On time
## 05:55  Newbury                                 1     On time
## 05:58  Bristol Temple Meads                    11A   On time
## 06:06  Southampton Central                     8B    On time
## 06:11  London Paddington                       13    On time
## 06:12  Bedwyn                                  11A   On time
## 06:14  Staines                                 5     On time
## 06:16  London Paddington                       9B    On time
## 06:18  Didcot Parkway                          15    On time
## 06:25  London Paddington                       9     On time
## 06:28  Oxford                                  11A   On time
## 06:31  Basingstoke                             2     On time
## 06:31  Bristol Temple Meads                    10    On time
## 06:41  Bedwyn                                  11A   On time
## 06:42  London Paddington                       14    On time
## 06:46  Didcot Parkway                          15    On time
## 06:48  London Waterloo                         6     On time
## 06:48  Swansea                                 10    On time
## 06:51  Basingstoke                             1     On time
## 06:51  Gatwick Airport                         5     On time
## 06:51  London Paddington                       9     On time
## 06:53  Worcester Shrub Hill                    10A   On time
## 06:54  London Paddington                       8     On time
## 06:55  London Paddington                       13    On time
## 06:59  Bristol Temple Meads                    11    On time
## 07:00  London Paddington                       14    On time
## 07:01  Newbury                                 1     On time
## 05:05  Heathrow Airport T3 (Bus)               BUS   On time
## 05:35  Heathrow Airport T3 (Bus)               BUS   On time
## 06:00  Heathrow Airport T3 (Bus)               BUS   On time
## 06:35  Heathrow Airport T3 (Bus)               BUS   On time
## 07:05  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-21 05:06:26.702356
## Time   To                                      Plat  Expected
## 05:10  London Paddington                       14A   On time
## 05:12  Bedwyn                                  8B    On time
## 05:16  Newbury                                 12B   On time
## 05:19  Basingstoke                             12A   On time
## 05:31  Gatwick Airport                         15A   On time
##        via Guildford                           
## 05:35  London Paddington                       15    On time
## 05:39  London Waterloo                         5     On time
## 05:40  Basingstoke                             12B   On time
## 05:40  Oxford                                  9     On time
## 05:45  Abbey Wood                              14    On time
## 05:48  London Paddington                       10A   On time
## 05:49  Swansea                                 9B    On time
## 05:50  Didcot Parkway                          13    On time
## 05:50  Newbury                                 1     On time
## 05:55  Redhill                                 15A   On time
## 06:00  London Paddington                       11A   On time
## 06:09  London Waterloo                         6     On time
## 06:14  Abbey Wood                              14    On time
## 06:14  London Paddington                       11A   On time
## 06:14  Newbury                                 15    On time
## 06:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 06:18  Great Malvern                           9B    On time
## 06:19  London Paddington                       15    On time
## 06:20  Basingstoke                             12    On time
## 06:24  Abbey Wood                              13    On time
## 06:27  Gatwick Airport                         15A   On time
##        via Guildford                           
## 06:27  Totnes                                  9     On time
## 06:34  London Paddington                       10    On time
## 06:36  London Paddington                       11A   On time
## 06:37  Newbury                                 1     On time
## 06:39  London Waterloo                         5     On time
## 06:40  Basingstoke                             2     On time
## 06:42  London Paddington                       11A   On time
## 06:44  Abbey Wood                              13    On time
## 06:45  Birmingham New Street                   7     On time
## 06:48  London Paddington                       15    On time
## 06:50  London Paddington                       10    On time
## 06:51  Redhill                                 13    On time
## 06:53  Weston-super-Mare                       9     On time
## 06:54  Abbey Wood                              14    On time
## 06:56  Cheltenham Spa                          8     On time
## 06:56  London Paddington                       10A   On time
## 06:57  Basingstoke                             1     On time
## 07:01  Didcot Parkway                          14    On time
## 07:02  London Paddington                       11    On time
## 05:30  Heathrow Airport T3 (Bus)               BUS   On time
## 06:00  Heathrow Airport T3 (Bus)               BUS   On time
## 06:25  Heathrow Airport T3 (Bus)               BUS   On time
## 06:55  Heathrow Airport T3 (Bus)               BUS   On time
```
