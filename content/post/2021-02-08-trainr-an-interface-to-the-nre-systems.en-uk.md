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

## Example (Last rendered on 2024-01-13 19:04)

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
## Reading (RDG) Station Board on 2024-01-13 19:04:29.846317
## Time   From                                    Plat  Expected
## 19:01  Didcot Parkway                          15    19:03
## 19:01  Penzance                                11    On time
## 19:06  Bournemouth                             7B    On time
## 19:10  Abbey Wood                              14    On time
## 19:10  Bristol Temple Meads                    10    On time
## 19:11  London Paddington                       8     19:16
## 19:13  London Waterloo                         4     19:15
## 19:14  London Paddington                       13    19:16
## 19:15  London Paddington                       9     19:17
## 19:22  Basingstoke                             2     On time
## 19:23  London Paddington                       9     On time
## 19:24  Oxford                                  10    On time
## 19:26  London Paddington                       8     On time
## 19:28  Gatwick Airport                         5     On time
## 19:29  Newbury                                 11A   On time
## 19:31  Didcot Parkway                          15    On time
## 19:31  London Paddington                       7     On time
## 19:37  London Paddington                       8     On time
## 19:40  Abbey Wood                              14    On time
## 19:41  London Paddington                       9     On time
## 19:42  Manchester Piccadilly                   8     On time
## 19:43  London Waterloo                         4     On time
## 19:43  Newbury                                 13B   On time
## 19:44  London Paddington                       12    On time
## 19:46  London Paddington                       9     On time
## 19:48  Swansea                                 10    19:51
## 19:52  Basingstoke                             2     On time
## 19:55  Salisbury                               1     On time
## 19:57  Gatwick Airport                         5     On time
## 19:58  Great Malvern                           10    On time
## 19:58  Plymouth                                11    On time
## 20:01  Bristol Temple Meads                    12    On time
## 20:01  Didcot Parkway                          15    On time
## 20:06  York                                    3     On time
## 20:10  Bristol Temple Meads                    10    On time
## 20:11  Abbey Wood                              14    On time
## 20:11  Bournemouth                             13    On time
## 20:11  London Paddington                       8     On time
## 20:13  London Waterloo                         4     On time
## 20:15  London Paddington                       9     On time
## 20:16  London Paddington                       12    On time
## 20:16  Newbury                                 11    On time
## 20:22  Basingstoke                             2     On time
## 20:23  London Paddington                       9     On time
## 20:23  Oxford                                  10    On time
## 20:26  London Paddington                       7     On time
## 20:29  Didcot Parkway                          15    On time
## 20:33  Gatwick Airport                         14B   On time
## 20:34  Cheltenham Spa                          11    On time
## 20:38  London Paddington                       9     On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:40  Abbey Wood                              14    On time
## 20:41  London Waterloo                         6     On time
## 20:41  Newbury                                 1     On time
## 20:44  London Paddington                       13    On time
## 20:45  London Paddington                       9     On time
## 20:46  Carmarthen                              11    On time
## 20:49  Basingstoke                             8A    On time
## 20:53  London Paddington                       12    On time
## 20:57  Gatwick Airport                         7B    On time
## 20:58  Great Malvern                           10    On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
## 20:10  Heathrow Airport T3 (Bus)               BUS   On time
## 20:40  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-13 19:04:31.898998
## Time   To                                      Plat  Expected
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       11    On time
## 19:09  London Waterloo                         6     On time
## 19:10  Newbury                                 1     On time
## 19:12  London Paddington                       10    On time
## 19:13  London Paddington                       15    On time
## 19:13  Swansea                                 8     19:15
## 19:15  Birmingham New Street                   7B    On time
##        via Coventry                            
## 19:18  Salisbury                               3     On time
## 19:19  Great Malvern                           9     On time
## 19:23  Didcot Parkway                          13    On time
## 19:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:25  Bristol Temple Meads                    9     On time
## 19:28  London Paddington                       10    On time
## 19:28  Plymouth                                8     On time
## 19:29  Abbey Wood                              14    On time
## 19:32  Basingstoke                             2     On time
## 19:32  London Paddington                       11A   On time
## 19:38  Taunton                                 8     On time
## 19:39  London Waterloo                         4     On time
## 19:41  Newbury                                 7     On time
## 19:43  London Paddington                       15    On time
## 19:43  Swansea                                 9     On time
## 19:48  Oxford                                  9     On time
## 19:50  London Paddington                       10    19:52
## 19:52  Bournemouth                             8     On time
## 19:53  Didcot Parkway                          12    On time
## 19:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:58  Cheltenham Spa                          8     On time
## 19:59  Abbey Wood                              14    On time
## 20:00  London Paddington                       10    On time
## 20:03  London Paddington                       11    On time
## 20:05  Basingstoke                             2     On time
## 20:05  London Paddington                       12    On time
## 20:09  London Waterloo                         4     On time
## 20:10  Newbury                                 7     On time
## 20:12  London Paddington                       10    On time
## 20:13  London Paddington                       15    On time
## 20:13  Swansea                                 8     On time
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 20:15  Salisbury                               1     On time
## 20:19  Great Malvern                           9     On time
## 20:20  London Paddington                       11    On time
## 20:23  Didcot Parkway                          12    On time
## 20:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:25  Bristol Temple Meads                    9     On time
## 20:27  London Paddington                       10    On time
## 20:28  Plymouth                                7     On time
## 20:29  Abbey Wood                              14    On time
## 20:35  London Paddington                       11    On time
## 20:37  Basingstoke                             2     On time
## 20:40  Swindon                                 9     On time
## 20:42  London Waterloo                         4     On time
## 20:43  London Paddington                       15    On time
## 20:48  London Paddington                       11    On time
## 20:48  Oxford                                  9     On time
## 20:52  Bournemouth                             7     On time
## 20:52  Didcot Parkway                          13    On time
## 20:55  Exeter St Davids                        12    On time
##        via Bristol                             
## 20:59  Abbey Wood                              14    On time
## 21:00  London Paddington                       10    On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:30  Heathrow Airport T3 (Bus)               BUS   On time
```
