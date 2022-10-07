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

## Example (Last rendered on 2022-10-07 06:06)

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
## Reading (RDG) Station Board on 2022-10-07 06:07:00
## Time   From                                    Plat  Expected
## 07:11  London Paddington                       12    On time
## 07:11  London Waterloo                         4     On time
## 07:27  London Paddington                       14    On time
## 07:43  Birmingham New Street                   7     On time
## 07:44  London Paddington                       14    On time
## 07:46  London Waterloo                         6     On time
## 07:56  London Paddington                       9     On time
## 07:57  London Paddington                       13    On time
## 08:07  Didcot Parkway                          15    On time
## 08:09  Bournemouth                             8     On time
## 08:09  Oxford                                  10    On time
## 08:11  London Waterloo                         4     On time
## 08:13  London Paddington                       14    On time
## 08:14  London Paddington                       9     On time
## 08:23  Bristol Parkway                         10    On time
## 08:29  London Paddington                       14    On time
## 08:36  London Paddington                       8     On time
## 08:39  Bristol Temple Meads                    11    On time
## 08:42  Basingstoke                             2     On time
## 08:42  London Waterloo                         6     On time
## 08:43  London Paddington                       9     On time
## 08:45  London Paddington                       12    On time
## 08:46  Manchester Piccadilly                   7B    On time
## 08:48  Swindon                                 10    On time
## 08:55  London Paddington                       8     On time
## 08:56  London Paddington                       13    On time
## 09:01  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-07 06:07:04
## Time   To                                      Plat  Expected
## 07:11  London Waterloo                         6     On time
## 07:13  London Paddington                       14    On time
## 07:14  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 07:26  London Paddington                       13    On time
## 07:37  Basingstoke                             7     On time
## 07:38  Cardiff Central                         9     On time
## 07:40  Ealing Broadway                         14    On time
## 07:42  London Waterloo                         4     On time
## 07:49  Oxford                                  8     On time
## 07:51  London Paddington                       15    On time
## 07:52  Bournemouth                             7     On time
## 07:52  Didcot Parkway                          13    On time
## 07:56  Ealing Broadway                         14    On time
## 08:00  Plymouth                                9     On time
##        via Bristol                             
## 08:10  Ealing Broadway                         13    On time
## 08:11  London Waterloo                         6     On time
## 08:14  Bristol Parkway                         9     On time
## 08:14  London Paddington                       10    On time
## 08:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 08:23  Basingstoke                             2     On time
## 08:25  Ealing Broadway                         14    On time
## 08:25  London Paddington                       10    On time
## 08:38  Cardiff Central                         8     On time
## 08:42  Ealing Broadway                         14    On time
## 08:42  London Paddington                       11    On time
## 08:42  London Waterloo                         4     On time
## 08:46  Oxford                                  9     On time
## 08:49  London Paddington                       10    On time
## 08:52  Bournemouth                             7B    On time
## 08:53  Didcot Parkway                          15    On time
## 08:57  Ealing Broadway                         12    On time
## 08:57  Plymouth                                8     On time
##        via Bristol
```
