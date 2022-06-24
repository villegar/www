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

## Example (Last rendered on 2022-06-24 06:03)

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
## Reading (RDG) Station Board on 2022-06-24 06:03:59
## Time   From                                    Plat  Expected
## 07:38  London Paddington                       9     On time
## 07:43  Didcot Parkway                          15    On time
## 07:54  Oxford                                  11A   On time
## 07:56  London Paddington                       9     On time
## 08:10  Swindon                                 15    On time
## 08:11  London Paddington                       9     On time
## 08:13  London Paddington                       14    On time
## 08:16  London Paddington                       12    On time
## 08:16  London Paddington                       9B    On time
## 08:18  Bristol Parkway                         10    On time
## 08:22  Newbury                                 3     On time
## 08:27  London Paddington                       7     On time
## 08:29  London Paddington                       14    On time
## 08:32  Staines                                 6     On time
## 08:39  Bristol Temple Meads                    11    On time
## 08:41  London Paddington                       8     On time
## 08:42  Basingstoke                             2     On time
## 08:45  Didcot Parkway                          14    On time
## 08:45  London Paddington                       12    On time
## 08:55  London Paddington                       8     On time
## 08:56  London Paddington                       13    On time
## 09:01  Didcot Parkway                          15    On time
## 08:26  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-24 06:04:02
## Time   To                                      Plat  Expected
## 07:03  Penzance                                7     On time
## 07:10  Newbury                                 1     On time
## 07:17  London Paddington                       14    On time
## 07:18  Great Malvern                           8     On time
## 07:25  Didcot Parkway                          12    On time
## 07:25  Redhill                                 15    On time
## 07:29  Ealing Broadway                         14    On time
## 07:37  Basingstoke                             2     On time
## 07:39  Cardiff Central                         9     On time
## 07:40  Ealing Broadway                         13    On time
## 07:44  Castle Cary                             8     On time
## 07:46  London Paddington                       15    On time
## 07:51  Didcot Parkway                          12    On time
## 07:54  Bedwyn                                  13B   On time
## 07:54  London Waterloo                         6     On time
## 07:56  London Paddington                       11A   On time
## 07:57  Ealing Broadway                         14    On time
## 08:00  Bristol Temple Meads                    9     On time
## 08:03  Newbury                                 15B   On time
## 08:13  Swansea                                 9     On time
## 08:17  London Paddington                       15    On time
## 08:19  Great Malvern                           9B    On time
## 08:20  London Paddington                       10    On time
## 08:20  Redhill                                 13A   On time
## 08:23  Basingstoke                             13B   On time
## 08:24  London Waterloo                         4     On time
## 08:25  Ealing Broadway                         14    On time
## 08:26  Didcot Parkway                          12    On time
## 08:29  Penzance                                7     On time
## 08:41  London Paddington                       11    On time
## 08:42  Ealing Broadway                         14    On time
## 08:43  Cardiff Central                         8     On time
## 08:53  Didcot Parkway                          14    On time
## 08:54  London Waterloo                         6     On time
## 08:57  Bristol Temple Meads                    8     On time
## 08:57  Ealing Broadway                         12    On time
## 07:10  Heathrow Central Bus Stn                BUS   On time
## 07:45  Heathrow Central Bus Stn                BUS   On time
## 08:20  Heathrow Central Bus Stn                BUS   On time
## 08:55  Heathrow Central Bus Stn                BUS   On time
```
