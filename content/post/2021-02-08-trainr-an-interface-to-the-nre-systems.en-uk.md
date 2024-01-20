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

## Example (Last rendered on 2024-01-20 09:04)

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
## Reading (RDG) Station Board on 2024-01-20 09:04:17.585837
## Time   From                                    Plat  Expected
## 08:58  Hereford                                10    09:01
## 09:01  Didcot Parkway                          15A   On time
## 09:03  Plymouth                                11    On time
## 09:07  Bournemouth                             13B   On time
## 09:09  Bristol Temple Meads                    10A   On time
## 09:10  London Paddington                       14    On time
## 09:11  London Paddington                       8     On time
## 09:11  London Waterloo                         4     On time
## 09:14  London Paddington                       12B   On time
## 09:16  London Paddington                       9B    On time
## 09:16  Swansea                                 10    On time
## 09:19  Basingstoke                             2     On time
## 09:23  London Paddington                       9B    Delayed
## 09:24  Newbury                                 11A   On time
## 09:24  Oxford                                  10A   On time
## 09:26  London Paddington                       7     On time
## 09:28  Guildford                               5     On time
## 09:30  London Paddington                       8B    On time
## 09:31  Didcot Parkway                          15A   On time
## 09:33  Cheltenham Spa                          11    09:37
## 09:40  Bristol Temple Meads                    10    On time
## 09:40  London Paddington                       14    On time
## 09:40  London Paddington                       9     On time
## 09:41  Newbury                                 1     On time
## 09:41  Nottingham                              8B    On time
## 09:43  London Waterloo                         6     On time
## 09:43  Plymouth                                11    09:45
## 09:44  London Paddington                       12B   On time
## 09:45  London Paddington                       9B    On time
## 09:47  Basingstoke                             2     On time
## 09:48  Swansea                                 10    On time
## 09:55  London Paddington                       8     On time
## 09:57  Guildford                               4     On time
## 09:58  Great Malvern                           10    On time
## 10:01  Didcot Parkway                          15A   On time
## 10:04  Plymouth                                11    On time
## 10:07  Bournemouth                             13B   On time
## 10:09  Bristol Temple Meads                    10    On time
## 10:11  London Paddington                       9     On time
## 10:11  London Waterloo                         5     On time
## 10:13  London Paddington                       14    On time
## 10:13  London Paddington                       8     On time
## 10:13  Worcester Foregate Street               11A   On time
## 10:16  London Paddington                       12B   On time
## 10:18  Swansea                                 10    On time
## 10:19  Basingstoke                             2     On time
## 10:26  London Paddington                       7     On time
## 10:28  Guildford                               4     On time
## 10:28  Oxford                                  10    On time
## 10:31  Didcot Parkway                          15A   On time
## 10:31  London Paddington                       8B    On time
## 10:31  Newbury                                 11A   On time
## 10:33  Cheltenham Spa                          10A   On time
## 10:38  London Paddington                       9     On time
## 10:40  Bristol Temple Meads                    10    On time
## 10:41  London Paddington                       14    On time
## 10:42  Manchester Piccadilly                   7     On time
## 10:42  Newbury                                 1     On time
## 10:43  London Paddington                       9     On time
## 10:43  London Waterloo                         6     On time
## 10:44  London Paddington                       12B   On time
## 10:46  Carmarthen                              10    On time
## 10:49  Basingstoke                             2     On time
## 10:57  Guildford                               5     On time
## 10:58  Great Malvern                           10    On time
## 10:59  London Paddington                       7     On time
## 09:15  Heathrow Airport T3 (Bus)               BUS   On time
## 09:45  Heathrow Airport T3 (Bus)               BUS   On time
## 10:15  Heathrow Airport T3 (Bus)               BUS   On time
## 10:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-20 09:04:19.907732
## Time   To                                      Plat  Expected
## 09:00  London Paddington                       10    09:03
## 09:05  Newbury                                 1     On time
## 09:06  London Paddington                       11    On time
## 09:09  London Waterloo                         6     On time
## 09:10  Basingstoke                             2     On time
## 09:12  London Paddington                       15A   On time
## 09:12  London Paddington                       10A   On time
## 09:13  Carmarthen                              8     On time
## 09:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 09:19  Great Malvern                           9B    On time
## 09:20  London Paddington                       10    On time
## 09:23  Didcot Parkway                          12B   On time
## 09:24  Guildford                               5     On time
## 09:25  Bristol Temple Meads                    9B    Delayed
## 09:25  London Paddington                       11A   On time
## 09:28  London Paddington                       10A   On time
## 09:29  Ealing Broadway                         14    On time
## 09:29  Plymouth                                7     On time
## 09:33  Newbury                                 8B    On time
## 09:35  London Paddington                       11    09:38
## 09:37  Basingstoke                             2     On time
## 09:39  London Waterloo                         4     On time
## 09:42  London Paddington                       10    On time
## 09:42  Swindon                                 9     On time
## 09:43  London Paddington                       15A   On time
## 09:45  London Paddington                       11    On time
## 09:47  Oxford                                  9B    On time
## 09:50  London Paddington                       10    On time
## 09:52  Bournemouth                             8B    On time
## 09:53  Didcot Parkway                          12B   On time
## 09:54  Guildford                               5     On time
## 09:55  Bristol Temple Meads                    9     On time
## 09:58  Cheltenham Spa                          8     On time
## 09:59  Ealing Broadway                         14    On time
## 10:00  London Paddington                       10    On time
## 10:05  London Paddington                       11    On time
## 10:07  Basingstoke                             2     On time
## 10:09  London Waterloo                         6     On time
## 10:12  London Paddington                       10    On time
## 10:12  Newbury                                 1     On time
## 10:13  London Paddington                       15A   On time
## 10:13  Swansea                                 9     On time
## 10:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 10:17  London Paddington                       11A   On time
## 10:18  Hereford                                8     On time
## 10:20  London Paddington                       10    On time
## 10:24  Didcot Parkway                          12B   On time
## 10:24  Guildford                               4     On time
## 10:25  Bristol Temple Meads                    9     On time
## 10:29  Ealing Broadway                         14    On time
## 10:30  London Paddington                       10    On time
## 10:30  Penzance                                7     On time
## 10:32  London Paddington                       11A   On time
## 10:33  Newbury                                 8B    On time
## 10:35  London Paddington                       10A   On time
## 10:37  Basingstoke                             2     On time
## 10:39  London Waterloo                         5     On time
## 10:40  Swindon                                 9     On time
## 10:42  London Paddington                       10    On time
## 10:43  London Paddington                       15A   On time
## 10:45  Oxford                                  9     On time
## 10:50  Didcot Parkway                          12B   On time
## 10:50  London Paddington                       10    On time
## 10:52  Bournemouth                             7     On time
## 10:54  Guildford                               4     On time
## 10:55  Bristol Temple Meads                    9     On time
## 10:58  Cheltenham Spa                          8     On time
## 10:59  Ealing Broadway                         14    On time
## 11:00  London Paddington                       10    On time
## 11:01  Paignton                                7     On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
```
