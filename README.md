# PollingCoordsExtractor
`PollingCoordsExtractor` is a wrapper around [Google Maps API](https://developers.google.com/maps/). It takes in a list of addresses as a single file with an address in each line.
Since it was developed for retreiving the coordinates of Polling Locations, it's named "PollingCoordsExtractor". However, it can be used
to extract coordinates of any location as long as the addresses are provided in the specified format.

This also returns additional attributes of the queried locations such as "Formatted Address" - address in the standard format and 
"Classifiers" - a ```list``` of location type (eg., place of worship, establishment, etc). 

## Requirements
This program requires [python2.7](https://www.python.org/download/releases/2.7/)
This program requires the following libraries:
1. [urllib](https://docs.python.org/3/library/urllib.html)
2. [urllib2](https://docs.python.org/2/library/urllib2.html)
3. [sys](https://docs.python.org/2/library/sys.html)
4. [json](https://docs.python.org/2/library/json.html)

## Usage
#### Create the extractor
```python
ple = PollingLocationExtractor("YOUR_API_KEY")
```
#### Read Addresses from input file
```python
filename = "addressFile.txt"
ple.readAddressesFromFile(filename)
```
#### Extract Locations' coordinates from json result returned by the API
```python
ple.extractCoords()
```
#### Write the extracted coordinates to an output file
```python
filename = "locationAttrs.tsv"
ple.writeLocationsToFile(filename)
```

## Limit
Google Maps limits the use of its API to 2500 free requests per day.
From Google Maps API web page -

>Users of the standard API:
  >1. 2,500 free requests per day, calculated as the sum of client-side and server-side queries.
  >2. 50 requests per second, calculated as the sum of client-side and server-side queries.
  
## Test
A test file named "PollingLocationTest.txt" has been provided to specify the format of input files.
