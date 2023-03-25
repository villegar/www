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

## Example (Last rendered on 2023-03-25 06:03)

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
## Reading (RDG) Station Board on 2023-03-25 06:03:15
## Time   From                                    Plat  Expected
## 06:07  London Paddington                       14    On time
## 06:12  Didcot Parkway                          15    On time
## 06:13  Virginia Water                          4     On time
## 06:15  London Paddington                       12B   On time
## 06:16  Oxford                                  10A   On time
## 06:17  London Paddington                       9     On time
## 06:32  Didcot Parkway                          15A   On time
## 06:39  London Paddington                       14    On time
## 06:41  Bristol Temple Meads                    10    On time
## 06:46  Basingstoke                             2     On time
## 06:46  London Paddington                       9B    On time
## 06:47  London Paddington                       12    On time
## 06:48  London Waterloo                         -     Delayed
## 06:48  London Waterloo                         -     Cancelled
## 06:48  Swansea                                 10    On time
## 06:53  London Paddington                       9     On time
## 06:55  Oxford                                  10A   On time
## 06:57  Bedwyn                                  14B   On time
## 07:03  Didcot Parkway                          15    On time
## 07:04  Gatwick Airport                         5     On time
## 07:06  Southampton Central                     13B   On time
## 07:08  Abbey Wood                              14    On time
## 07:11  Bristol Temple Meads                    10    On time
## 07:11  London Paddington                       9     On time
## 07:17  London Paddington                       9B    On time
## 07:20  Basingstoke                             2     On time
## 07:21  London Paddington                       13B   On time
## 07:23  Newbury                                 11    On time
## 07:25  London Paddington                       9     On time
## 07:25  Oxford                                  10A   On time
## 07:30  London Waterloo                         -     Cancelled
## 07:30  London Waterloo                         -     Delayed
## 07:32  Didcot Parkway                          15    On time
## 07:33  Abbey Wood                              14    On time
## 07:33  London Paddington                       7     On time
## 07:33  Swindon                                 10    On time
## 07:38  Newbury                                 1     On time
## 07:40  Bristol Temple Meads                    10    On time
## 07:42  Birmingham New Street                   13    On time
## 07:43  London Paddington                       12    On time
## 07:45  Swansea                                 10    On time
## 07:47  London Paddington                       9B    On time
## 07:51  Gatwick Airport                         4     On time
## 07:51  London Paddington                       8B    On time
## 07:54  Great Malvern                           10    On time
## 07:55  London Paddington                       9     On time
## 07:57  Basingstoke                             2     On time
## 08:00  Salisbury                               3     On time
## 06:13  Heathrow Central Bus Stn                -     On time
## 07:25  Heathrow Central Bus Stn                BUS   On time
## 07:57  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-25 06:03:19
## Time   To                                      Plat  Expected
## 06:07  Basingstoke                             15B   On time
## 06:09  London Waterloo                         5     On time
## 06:12  Newbury                                 12B   On time
## 06:14  London Paddington                       15    On time
## 06:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 06:19  Didcot Parkway                          12B   On time
## 06:19  Great Malvern                           9     On time
## 06:19  Redhill                                 15A   On time
## 06:20  London Paddington                       10A   On time
## 06:24  Abbey Wood                              14    On time
## 06:34  Newbury                                 14B   On time
## 06:35  London Paddington                       15A   On time
## 06:37  Basingstoke                             13A   On time
## 06:39  London Waterloo                         4     On time
## 06:44  London Paddington                       10    On time
## 06:49  Oxford                                  9B    On time
## 06:50  London Paddington                       10    On time
## 06:53  Didcot Parkway                          12    On time
## 06:54  Abbey Wood                              14    On time
## 06:55  Bristol Temple Meads                    9     On time
## 06:58  London Paddington                       10A   On time
## 07:01  Gatwick Airport                         13    On time
##        via Guildford                           
## 07:07  Basingstoke                             2     On time
## 07:09  London Waterloo                         6     On time
## 07:12  London Paddington                       10    On time
## 07:12  Newbury                                 12B   On time
## 07:13  Swansea                                 9     On time
## 07:15  Ealing Broadway                         15    On time
## 07:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 07:20  Great Malvern                           9B    On time
## 07:20  Redhill                                 5     On time
## 07:24  Abbey Wood                              14    On time
## 07:24  London Paddington                       11    On time
## 07:26  Didcot Parkway                          13B   On time
## 07:26  London Paddington                       10A   On time
## 07:27  Bristol Temple Meads                    9     On time
## 07:32  Basingstoke                             2     On time
## 07:34  London Paddington                       10    On time
## 07:35  Newbury                                 7     On time
## 07:39  London Waterloo                         4     On time
## 07:42  London Paddington                       10    On time
## 07:45  Ealing Broadway                         15    On time
## 07:47  London Paddington                       10    On time
## 07:50  Oxford                                  9B    On time
## 07:53  Cheltenham Spa                          8B    On time
## 07:53  Didcot Parkway                          12    On time
## 07:54  Abbey Wood                              14    On time
## 07:56  London Paddington                       10    On time
## 07:57  Bristol Temple Meads                    9     On time
## 08:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 08:02  Newbury                                 1     On time
## 06:30  Heathrow Airport T3 (Bus)               BUS   On time
## 07:00  Heathrow Airport T3 (Bus)               BUS   On time
## 07:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:00  Heathrow Airport T3 (Bus)               BUS   On time
```
