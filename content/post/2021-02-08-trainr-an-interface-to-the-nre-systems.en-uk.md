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

## Example (Last rendered on 2021-04-03 14:03)

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
## Reading (RDG) Station Board on 2021-04-03 14:03:26
## Time   From                                    Plat  Expected
## 15:01  Didcot Parkway                          15    On time
## 15:07  London Paddington                       9     On time
## 15:10  Southampton Central                     13    On time
## 15:11  London Paddington                       8     On time
## 15:13  London Paddington                       14    On time
## 15:14  London Waterloo                         4     On time
## 15:16  London Paddington                       9     On time
## 15:17  Penzance                                10    On time
## 15:20  Bedwyn                                  11    On time
## 15:26  London Paddington                       7     On time
## 15:32  London Paddington                       7B    On time
## 15:33  Cheltenham Spa                          11    On time
## 15:38  Newbury                                 1     On time
## 15:39  Manchester Piccadilly                   13    On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:43  London Paddington                       14    On time
## 15:44  London Paddington                       12    On time
## 15:44  London Waterloo                         6     On time
## 15:47  Swansea                                 10    On time
## 15:53  London Paddington                       9     On time
## 15:54  Hereford                                10    On time
## 15:57  Ash                                     4     On time
## 15:57  Basingstoke                             2     On time
## 16:01  Didcot Parkway                          15    On time
## 16:11  London Paddington                       9     On time
## 16:13  London Paddington                       8     On time
## 16:13  London Paddington                       14    On time
## 16:14  London Waterloo                         5     On time
## 16:17  Westbury                                11    On time
## 16:18  London Paddington                       9     On time
## 16:24  Plymouth                                10    On time
## 16:27  Bedwyn                                  11    On time
## 16:31  London Paddington                       7B    On time
## 16:39  Manchester Piccadilly                   7     On time
## 16:41  Bristol Temple Meads                    10    On time
## 16:41  Newbury                                 1     On time
## 16:43  London Paddington                       14    On time
## 16:44  London Paddington                       12    On time
## 16:44  London Waterloo                         6     On time
## 16:46  Swansea                                 10    On time
## 16:53  London Paddington                       9     On time
## 16:54  Worcester Foregate Street               10    On time
## 16:56  Basingstoke                             2     On time
## 16:56  London Paddington                       8     On time
## 16:57  Ash                                     5     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-04-03 14:03:29
## Time   To                                      Plat  Expected
## 15:09  Penzance                                9     On time
## 15:10  Newbury                                 1     On time
## 15:12  London Waterloo                         6     On time
## 15:13  Swansea                                 8     On time
## 15:15  Ealing Broadway                         15    On time
## 15:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 15:19  Great Malvern                           9     On time
## 15:19  London Paddington                       10    On time
## 15:22  Ealing Broadway                         14    On time
## 15:23  London Paddington                       11    On time
## 15:28  Westbury                                7     On time
## 15:34  Bedwyn                                  7B    On time
## 15:35  Ash                                     5     On time
## 15:35  London Paddington                       11    On time
## 15:42  London Paddington                       10    On time
## 15:42  London Waterloo                         4     On time
## 15:50  London Paddington                       10    On time
## 15:52  Basingstoke                             2     On time
## 15:52  Ealing Broadway                         14    On time
## 15:53  Didcot Parkway                          12    On time
## 15:55  Bristol Temple Meads                    9     On time
## 15:56  London Paddington                       10    On time
## 16:10  Newbury                                 1     On time
## 16:12  London Waterloo                         6     On time
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:17  Plymouth                                8     On time
## 16:19  London Paddington                       11    On time
## 16:20  Great Malvern                           9     On time
## 16:22  Ealing Broadway                         14    On time
## 16:25  London Paddington                       10    On time
## 16:30  London Paddington                       11    On time
## 16:34  Bedwyn                                  7B    On time
## 16:35  Ash                                     4     On time
## 16:41  London Paddington                       10    On time
## 16:42  London Waterloo                         5     On time
## 16:48  London Paddington                       10    On time
## 16:49  Southampton Central                     7     On time
## 16:52  Basingstoke                             2     On time
## 16:52  Ealing Broadway                         14    On time
## 16:53  Didcot Parkway                          12    On time
## 16:55  Bristol Temple Meads                    9     On time
## 16:56  London Paddington                       10    On time
## 16:58  Cheltenham Spa                          8     On time
```
