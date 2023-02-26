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

## Example (Last rendered on 2023-02-26 22:03)

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
## Reading (RDG) Station Board on 2023-02-26 22:03:22
## Time   From                                    Plat  Expected
## 21:53  Great Malvern                           11    22:02
## 22:09  London Paddington                       9     On time
## 22:10  Weston-super-Mare                       10    On time
## 22:11  London Paddington                       12B   On time
## 22:13  Didcot Parkway                          13    On time
## 22:15  London Paddington                       9     On time
## 22:27  Abbey Wood                              14    On time
## 22:29  Henley-on-Thames                        13A   On time
## 22:33  Basingstoke                             13A   On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:40  London Paddington                       9     On time
## 22:49  Swansea                                 11A   On time
## 22:52  Great Malvern                           10    On time
## 22:58  Penzance                                11    On time
## 23:00  Abbey Wood                              14    On time
## 23:08  Didcot Parkway                          10    On time
## 23:12  London Paddington                       9     On time
## 23:25  London Paddington                       7     On time
## 23:26  London Paddington                       13    On time
## 23:39  Plymouth                                11A   On time
## 22:03  Bracknell                               BUS   On time
## 22:07  Bedwyn                                  BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:19  Bracknell                               BUS   On time
## 22:33  Bracknell                               BUS   On time
## 22:38  Guildford                               BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 22:49  Bracknell                               BUS   On time
## 22:49  Newbury                                 BUS   On time
## 23:03  Bracknell                               BUS   On time
## 23:08  Guildford                               BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
## 23:19  Bracknell                               BUS   On time
## 23:33  Bracknell                               BUS   On time
## 23:49  Bracknell                               BUS   On time
## 23:50  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-26 22:03:26
## Time   To                                      Plat  Expected
## 21:55  London Paddington                       11    22:03
## 22:10  Swansea                                 9     On time
## 22:12  Didcot Parkway                          12B   On time
## 22:13  London Paddington                       10    On time
## 22:16  Worcester Shrub Hill                    9     On time
## 22:22  Ealing Broadway                         12    On time
## 22:41  Bristol Temple Meads                    9     On time
## 22:50  London Paddington                       11A   On time
## 22:55  Ealing Broadway                         14    On time
## 23:00  London Paddington                       11    On time
## 23:02  London Paddington                       10    On time
## 23:10  Ealing Broadway                         10    On time
## 23:15  Bristol Parkway                         9     On time
## 23:16  Ealing Broadway                         14    On time
## 23:20  Didcot Parkway                          8     On time
## 23:37  Bristol Temple Meads                    7     On time
## 23:44  London Paddington                       11A   On time
## 22:05  Bracknell                               BUS   On time
## 22:21  Bracknell                               BUS   On time
## 22:25  Guildford                               BUS   On time
## 22:35  Bracknell                               BUS   On time
## 22:46  Newbury                                 BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:03  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 23:18  Bracknell                               BUS   On time
## 23:31  Bracknell                               BUS   On time
## 23:52  Staines                                 BUS   On time
```
