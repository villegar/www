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

## Example (Last rendered on 2023-03-18 16:03)

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
## Reading (RDG) Station Board on 2023-03-18 16:03:58
## Time   From                                    Plat  Expected
## 16:11  London Paddington                       12B   On time
## 16:14  London Paddington                       9     On time
## 16:19  Cardiff Central                         11    16:27
## 16:24  Oxford                                  10    On time
## 16:28  Newbury                                 11A   On time
## 16:31  Didcot Parkway                          15A   On time
## 16:33  Abbey Wood                              14    On time
## 16:33  London Paddington                       7B    On time
## 16:39  Bristol Temple Meads                    10    On time
## 16:39  Manchester Piccadilly                   7     On time
## 16:41  Newbury                                 1     On time
## 16:46  London Paddington                       9     On time
## 16:46  Swindon                                 10A   On time
## 16:50  Basingstoke                             2     On time
## 16:52  London Paddington                       8     On time
## 16:56  London Paddington                       9     On time
## 17:03  Abbey Wood                              14    On time
## 17:05  Southampton Central                     8     On time
## 17:10  London Paddington                       12B   On time
## 17:16  London Paddington                       9     On time
## 17:21  Cardiff Central                         11    On time
## 17:24  Oxford                                  10    On time
## 17:28  Newbury                                 11A   On time
## 17:31  Didcot Parkway                          15A   On time
## 17:33  Abbey Wood                              14    On time
## 17:33  London Paddington                       7B    On time
## 17:36  London Paddington                       9     On time
## 17:38  Exeter St Davids                        10    On time
## 17:41  Newbury                                 1     On time
## 17:47  London Paddington                       9     On time
## 17:50  Basingstoke                             13B   On time
## 17:53  Bristol Parkway                         11A   On time
## 17:55  London Paddington                       8     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-18 16:04:02
## Time   To                                      Plat  Expected
## 16:12  Newbury                                 1     On time
## 16:14  Bristol Parkway                         9     On time
## 16:21  London Paddington                       11    16:28
## 16:23  Didcot Parkway                          12B   On time
## 16:24  Abbey Wood                              14    On time
## 16:26  London Paddington                       10    On time
## 16:31  London Paddington                       11A   On time
## 16:34  Newbury                                 7B    On time
## 16:37  Basingstoke                             2     On time
## 16:42  London Paddington                       10    On time
## 16:45  Ealing Broadway                         15A   On time
## 16:48  London Paddington                       10A   On time
## 16:48  Oxford                                  9     On time
## 16:52  Southampton Central                     7     On time
## 16:54  Abbey Wood                              14    On time
## 16:54  Cardiff Central                         8     On time
## 16:58  Bristol Temple Meads                    9     On time
## 17:12  Newbury                                 1     On time
## 17:16  Bristol Parkway                         9     On time
## 17:22  London Paddington                       11    On time
## 17:23  Didcot Parkway                          12B   On time
## 17:24  Abbey Wood                              14    On time
## 17:27  London Paddington                       10    On time
## 17:32  London Paddington                       11A   On time
## 17:35  Newbury                                 7B    On time
## 17:38  Basingstoke                             2     On time
## 17:38  Bristol Parkway                         9     On time
## 17:41  London Paddington                       10    On time
## 17:45  Ealing Broadway                         15A   On time
## 17:48  Oxford                                  9     On time
## 17:54  Abbey Wood                              14    On time
## 17:55  London Paddington                       11A   On time
## 17:57  Swindon                                 8     On time
```
