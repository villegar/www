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

## Example (Last rendered on 2024-04-13 05:07)

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
## Reading (RDG) Station Board on 2024-04-13 05:07:42.773916
## Time   From                                    Plat  Expected
## 06:10  London Paddington                       14    On time
## 06:12  Didcot Parkway                          15    On time
## 06:13  Staines                                 4     On time
## 06:15  London Paddington                       9     06:19
## 06:17  Oxford                                  10A   On time
## 06:18  London Paddington                       12B   On time
## 06:40  Bristol Temple Meads                    10    On time
## 06:40  London Paddington                       14    On time
## 06:41  Didcot Parkway                          15    On time
## 06:44  London Paddington                       13B   On time
## 06:45  London Paddington                       9B    On time
## 06:46  Basingstoke                             2     On time
## 06:48  London Waterloo                         6     On time
## 06:48  Swansea                                 10    On time
## 06:53  London Paddington                       9     On time
## 06:56  Oxford                                  10A   On time
## 06:58  Bedwyn                                  13B   On time
## 07:04  Didcot Parkway                          15    On time
## 07:10  Bristol Temple Meads                    10    On time
## 07:10  London Paddington                       14    On time
## 07:11  London Paddington                       9B    On time
## 07:11  London Waterloo                         4     On time
## 07:14  London Paddington                       12    On time
## 07:15  London Paddington                       8B    On time
## 07:19  Basingstoke                             2     On time
## 07:22  Newbury                                 11A   On time
## 07:23  London Paddington                       9     On time
## 07:24  Oxford                                  10A   On time
## 07:30  Guildford                               5     On time
## 07:31  London Paddington                       7B    On time
## 07:32  Didcot Parkway                          15    On time
## 07:33  Swindon                                 11    On time
## 07:38  Newbury                                 1     On time
## 07:40  Abbey Wood                              14    On time
## 07:41  Bristol Temple Meads                    10    On time
## 07:43  London Waterloo                         5     On time
## 07:44  London Paddington                       12    On time
## 07:45  London Paddington                       9     On time
## 07:45  Swansea                                 11    On time
## 07:53  London Paddington                       9     On time
## 07:55  London Paddington                       7     On time
## 07:56  Basingstoke                             2     On time
## 07:57  Great Malvern                           10    On time
## 06:35  Heathrow Airport T3 (Bus)               BUS   On time
## 07:05  Heathrow Airport T3 (Bus)               BUS   On time
## 07:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-04-13 05:07:46.890928
## Time   To                                      Plat  Expected
## 06:09  London Waterloo                         6     On time
## 06:12  Newbury                                 7B    On time
## 06:13  London Paddington                       15    On time
## 06:19  Didcot Parkway                          12B   On time
## 06:19  Great Malvern                           9     06:20
## 06:20  London Paddington                       10A   On time
## 06:24  Guildford                               5     On time
## 06:29  Abbey Wood                              14    On time
## 06:34  Newbury                                 1     On time
## 06:37  Basingstoke                             13A   On time
## 06:39  London Waterloo                         4     On time
## 06:44  London Paddington                       10    On time
## 06:45  London Paddington                       15    On time
## 06:49  Oxford                                  9B    On time
## 06:50  London Paddington                       10    On time
## 06:52  Didcot Parkway                          13B   On time
## 06:55  Bristol Temple Meads                    9     On time
## 06:58  London Paddington                       10A   On time
## 06:59  Abbey Wood                              14    On time
## 07:07  Basingstoke                             2     On time
## 07:09  London Waterloo                         6     On time
## 07:12  London Paddington                       10    On time
## 07:12  Newbury                                 7B    On time
## 07:13  Carmarthen                              9B    On time
## 07:13  London Paddington                       15    On time
## 07:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 07:19  Great Malvern                           8B    On time
## 07:24  Guildford                               15A   On time
## 07:24  London Paddington                       11A   On time
## 07:25  Bristol Temple Meads                    9     On time
## 07:26  Didcot Parkway                          12    On time
## 07:28  London Paddington                       10A   On time
## 07:29  Abbey Wood                              14    On time
## 07:32  Basingstoke                             2     On time
## 07:34  London Paddington                       11    On time
## 07:35  Newbury                                 7B    On time
## 07:39  London Waterloo                         4     On time
## 07:42  London Paddington                       10    On time
## 07:43  London Paddington                       15    On time
## 07:47  Oxford                                  9     On time
## 07:48  London Paddington                       11    On time
## 07:52  Didcot Parkway                          12    On time
## 07:55  Weston-super-Mare                       9     On time
## 07:58  Cheltenham Spa                          7     On time
## 07:59  Abbey Wood                              14    On time
## 07:59  London Paddington                       10    On time
## 08:02  Newbury                                 1     On time
## 08:06  Guildford                               5     On time
## 06:25  Heathrow Airport T3 (Bus)               BUS   On time
## 06:55  Heathrow Airport T3 (Bus)               BUS   On time
## 07:25  Heathrow Airport T3 (Bus)               BUS   On time
## 07:55  Heathrow Airport T3 (Bus)               BUS   On time
```
