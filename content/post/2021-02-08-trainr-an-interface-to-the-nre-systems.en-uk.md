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

## Example (Last rendered on 2024-01-20 19:04)

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
## Reading (RDG) Station Board on 2024-01-20 19:04:06.910649
## Time   From                                    Plat  Expected
## 17:48  Swansea                                 -     18:37
## 18:01  Didcot Parkway                          -     18:34
## 18:21  Bristol Parkway                         -     19:16
## 18:31  Didcot Parkway                          -     18:41
## 18:34  Cheltenham Spa                          -     Delayed
## 18:40  Bristol Temple Meads                    -     Delayed
## 18:41  London Paddington                       -     Delayed
## 18:43  London Paddington                       -     Delayed
## 18:44  London Paddington                       -     Cancelled
## 18:46  Carmarthen                              -     19:46
## 18:58  Great Malvern                           -     Delayed
## 18:58  London Paddington                       9     Delayed
## 19:01  Didcot Parkway                          -     Delayed
## 19:01  Penzance                                -     19:16
## 19:06  Bournemouth                             7B    On time
## 19:10  Bristol Temple Meads                    -     Delayed
## 19:11  London Paddington                       -     Cancelled
## 19:11  London Paddington                       -     Cancelled
## 19:11  London Waterloo                         4     On time
## 19:14  London Paddington                       -     Cancelled
## 19:15  London Paddington                       9     Delayed
## 19:22  Basingstoke                             2     On time
## 19:23  London Paddington                       9     19:26
## 19:24  Oxford                                  10    Delayed
## 19:26  London Paddington                       8     On time
## 19:28  Guildford                               5     On time
## 19:29  Newbury                                 11A   On time
## 19:31  Didcot Parkway                          15A   On time
## 19:31  London Paddington                       7B    On time
## 19:41  Bristol Temple Meads                    10    Delayed
## 19:41  London Paddington                       -     Cancelled
## 19:41  London Paddington                       9     On time
## 19:41  Manchester Piccadilly                   8B    On time
## 19:43  London Waterloo                         4     19:49
## 19:43  Newbury                                 13B   On time
## 19:44  London Paddington                       12B   On time
## 19:46  London Paddington                       9     On time
## 19:48  Swansea                                 10    Delayed
## 19:50  Basingstoke                             2     On time
## 19:53  London Paddington                       9     On time
## 19:57  Guildford                               5     On time
## 19:58  Great Malvern                           -     Cancelled
## 19:58  Plymouth                                11    On time
## 20:01  Didcot Parkway                          15A   On time
## 20:06  York                                    3     On time
## 20:10  Bristol Temple Meads                    10    Delayed
## 20:11  Bournemouth                             13    On time
## 20:11  London Paddington                       8     On time
## 20:11  London Paddington                       -     Cancelled
## 20:15  London Paddington                       9     On time
## 20:16  London Paddington                       12B   On time
## 20:16  London Waterloo                         4     On time
## 20:16  Newbury                                 11A   On time
## 20:22  Basingstoke                             2     On time
## 20:23  London Paddington                       9     On time
## 20:23  Oxford                                  10    On time
## 20:26  London Paddington                       7     On time
## 20:29  Didcot Parkway                          15A   On time
## 20:33  Guildford                               14B   On time
## 20:34  Cheltenham Spa                          11    On time
## 20:38  London Paddington                       9     On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:41  London Paddington                       -     Cancelled
## 20:41  London Waterloo                         6     On time
## 20:41  Newbury                                 1     On time
## 20:44  London Paddington                       13B   On time
## 20:45  London Paddington                       9     On time
## 20:46  Carmarthen                              11    On time
## 20:49  Basingstoke                             8A    On time
## 20:53  London Paddington                       9     On time
## 20:57  Guildford                               7B    On time
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
## Reading (RDG) Station Board on 2024-01-20 19:04:09.263486
## Time   To                                      Plat  Expected
## 17:50  London Paddington                       -     Delayed
## 18:13  London Paddington                       -     Cancelled
## 18:22  London Paddington                       -     Cancelled
## 18:35  London Paddington                       -     Delayed
## 18:42  London Paddington                       -     Delayed
## 18:43  London Paddington                       -     Delayed
## 18:43  Swansea                                 -     Delayed
## 18:47  Oxford                                  -     Delayed
## 18:49  London Paddington                       -     19:47
## 18:50  Didcot Parkway                          15A   Delayed
## 18:56  Bristol Temple Meads                    8B    Delayed
## 19:00  London Paddington                       -     Delayed
## 19:00  Swindon                                 9     Delayed
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       -     19:17
## 19:09  London Waterloo                         6     On time
## 19:10  Newbury                                 1     On time
## 19:12  London Paddington                       -     Delayed
## 19:13  London Paddington                       -     Delayed
## 19:13  Swansea                                 9     On time
## 19:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Wilmslow                 
## 19:19  Great Malvern                           9     Delayed
## 19:23  Didcot Parkway                          14A   On time
## 19:24  Guildford                               5     On time
## 19:25  Bristol Temple Meads                    9     19:27
## 19:28  London Paddington                       10    Delayed
## 19:28  Plymouth                                8     On time
## 19:29  Ealing Broadway                         -     Cancelled
## 19:32  Basingstoke                             2     On time
## 19:32  London Paddington                       11A   On time
## 19:38  Newbury                                 7B    On time
## 19:39  London Waterloo                         4     On time
## 19:42  London Paddington                       10    Delayed
## 19:43  London Paddington                       15A   On time
## 19:43  Swansea                                 9     On time
## 19:48  Oxford                                  9     On time
## 19:50  London Paddington                       10    Delayed
## 19:52  Bournemouth                             8B    On time
## 19:53  Didcot Parkway                          12B   On time
## 19:54  Guildford                               5     On time
## 19:55  Bristol Temple Meads                    9     On time
## 19:58  Cheltenham Spa                          8     On time
## 19:59  Ealing Broadway                         -     Cancelled
## 20:00  London Paddington                       -     Cancelled
## 20:03  London Paddington                       11    On time
## 20:05  Basingstoke                             2     On time
## 20:09  London Waterloo                         4     On time
## 20:10  Newbury                                 7     On time
## 20:12  London Paddington                       10    Delayed
## 20:13  London Paddington                       15A   On time
## 20:13  Swansea                                 8     On time
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 20:19  Great Malvern                           9     On time
## 20:20  London Paddington                       11A   On time
## 20:23  Didcot Parkway                          12B   On time
## 20:24  Guildford                               5     On time
## 20:25  Bristol Temple Meads                    9     On time
## 20:27  London Paddington                       10    On time
## 20:28  Plymouth                                7     On time
## 20:29  Ealing Broadway                         -     Cancelled
## 20:35  London Paddington                       11    On time
## 20:37  Basingstoke                             2     On time
## 20:40  Swindon                                 9     On time
## 20:42  London Waterloo                         4     On time
## 20:43  London Paddington                       15A   On time
## 20:48  London Paddington                       11    On time
## 20:48  Oxford                                  9     On time
## 20:52  Bournemouth                             7     On time
## 20:52  Didcot Parkway                          13B   On time
## 20:56  Exeter St Davids                        9     On time
##        via Bristol                             
## 20:59  Ealing Broadway                         -     Cancelled
## 21:00  London Paddington                       10    On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:30  Heathrow Airport T3 (Bus)               BUS   On time
```
