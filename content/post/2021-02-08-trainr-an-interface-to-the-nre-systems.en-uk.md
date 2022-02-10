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

## Example (Last rendered on 2022-02-10 18:04)

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
## Reading (RDG) Station Board on 2022-02-10 18:05:32
## Time   From                                    Plat  Expected
## 18:03  Didcot Parkway                          15A   18:00
## 18:08  Bournemouth                             12    18:05
## 18:09  Bristol Temple Meads                    11    On time
## 18:10  London Waterloo                         5     On time
## 18:11  London Paddington                       9     On time
## 18:13  London Paddington                       14    On time
## 18:20  Basingstoke                             2     On time
## 18:25  Newbury                                 11A   On time
## 18:26  London Paddington                       8     On time
## 18:26  Oxford                                  10A   On time
## 18:27  London Paddington                       7     On time
## 18:28  London Paddington                       13    On time
## 18:29  Didcot Parkway                          15A   On time
## 18:30  Cheltenham Spa                          11A   On time
## 18:30  London Paddington                       12B   On time
## 18:35  Newbury                                 1     On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:40  London Waterloo                         6     On time
## 18:42  London Paddington                       9     On time
## 18:43  London Paddington                       14    On time
## 18:43  Manchester Piccadilly                   8     On time
## 18:44  London Paddington                       12    On time
## 18:45  Redhill                                 5     On time
## 18:47  Swansea                                 10    On time
## 18:50  Basingstoke                             3     On time
## 18:53  London Paddington                       13B   On time
## 18:56  London Waterloo                         6     On time
## 18:57  Great Malvern                           10A   On time
## 18:57  London Paddington                       9B    On time
## 18:57  Penzance                                11    On time
## 18:58  London Paddington                       14    On time
## 18:59  London Paddington                       7     On time
## 19:04  Basingstoke                             2     On time
## 19:05  Didcot Parkway                          15A   On time
## 19:05  Gatwick Airport                         4     On time
## 19:10  Weston-super-Mare                       10    On time
## 19:11  London Paddington                       9     On time
## 19:13  London Paddington                       14    On time
## 19:15  London Paddington                       13    On time
## 19:15  London Waterloo                         6     On time
## 19:15  Newbury                                 1     On time
## 19:22  Newbury                                 11A   On time
## 19:25  Worcester Foregate Street               10A   On time
## 19:26  London Paddington                       8     On time
## 19:28  Didcot Parkway                          15A   On time
## 19:28  London Paddington                       14    On time
## 19:29  London Paddington                       7     On time
## 19:30  London Paddington                       12    On time
## 19:33  Redhill                                 4     On time
## 19:34  Basingstoke                             2     On time
## 19:34  London Paddington                       7B    On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:40  London Waterloo                         6     On time
## 19:41  London Paddington                       9     On time
## 19:41  Manchester Piccadilly                   7B    On time
## 19:43  London Paddington                       13    On time
## 19:45  London Paddington                       12    On time
## 19:46  Swansea                                 10    On time
## 19:53  London Paddington                       8B    On time
## 19:54  Worcester Foregate Street               10A   On time
## 19:55  London Paddington                       12    On time
## 19:55  Plymouth                                11    On time
## 19:56  London Paddington                       9     On time
## 19:58  London Waterloo                         6     On time
## 20:00  Basingstoke                             1     On time
## 20:03  Newbury                                 2     On time
## 20:04  Gatwick Airport                         4     On time
## 18:21  Heathrow Central Bus Stn                BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
```

```
## Error: '' does not exist in current working directory ('/Users/runner/work/www/www/content/post').
```

```r
print(rdg_dep)
```

```
## Error in print(rdg_dep): object 'rdg_dep' not found
```
