## Home Assisant sensor component for Afvalbeheer

Provides Home Assistant sensors for multiple Dutch waste collectors using REST API.
This sensor works with the ophaalkalender.be waste collector.

### Install:
Copy the files in the /custom_components/ophaalkalender/ folder to: [homeassistant]/config/custom_components/ophaalkalender/

Example config:

```yaml
  sensor:
    - platform: ophaalkalender
      resources:
        - restafval
        - tuinafval
        - papier
        - pmd
        - grofafval
      postcode: ?
      streetname: ?
      streetnumber: ?
```

### Resources
```
resources:
```
This is a list of fractions you want a sensor for. At least one option is required.
Resources options:
  - restafval
  - tuinafval
  - papier
  - pmd
  - grofafval

### Postcode
Postcode is required and is your own postcode

### Street name
Street name is required and is your own street name

### Street number
Street number is required and is your own street number

### Date format
```yaml
dateformat:
```
If you want to adjust the way the date is presented. You can do it using the dateformat option. All [python strftime options](http://strftime.org/) should work.
Default is '%d-%m-%Y', which will result in per example: 
```yaml
21-9-2019.
```
If you wish to remove the year and the dashes and want to show the name of the month abbreviated, you would provide '%d %b'. Which will result in: 
```yaml
21 Sep
```

### Date only
```yaml
dateonly: 1
```
If you don't want to add dayname, tomorrow or today in front of date activate this option. Default is 0.

## Custom updater
You can use the custom updater with this sensor

Home assistant 88 and higher:
```yaml
custom_updater:
  track:
    - components
  component_urls:
    - https://raw.githubusercontent.com/pippyn/Home-Assistant-Sensor-Afvalbeheer/master/custom_components.json
```
