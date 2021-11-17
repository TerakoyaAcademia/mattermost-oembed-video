# oEmbed plugin

This plugin renders oEmbed previews for the links that support them.

![oEmbed example](./public/oEmbed-example.png)

# Add your website to get preview
cd generator/oembed-spec/providers
create a <fileName>.yml
Inside the file, the structure be just like the following code: 

```
---
- provider_name: XYZ
  provider_url: https://xyz.com
  endpoints:
  - schemes:
    - https://xyz.com/w
    - https://xyz.com/w/*
    - https://xyz.com/api/v1/videos/*
    url: https://xyz.com/services/oembed
    example_urls:
    - https://xyz.com/services/oembed?url=https://xyz.com/w/eutte71SVkAi1tF7RtmUEe
    discovery: true
...
```

Add the website url from where you want to show the video.

## Update provider dimensions file

The plugin needs to know the expected dimensions of the embed
representation for every provider in advance. To fetch them, there is
a script in the `generator` folder that runs an example query per
provider and saves the dimensions for the provider from the response.

To run the script, first go to the `generator` folder and install the
node dependencies:

```sh
cd generator
npm install
```

and with the dependencies installed, run:

```sh
npm run generate
```

the script will write a `provider-dimensions.json` file that you can
use to replace the `webapp/src/provider-dimensions.json` file before
building the plugin.

# Build Plugin
```sh
cd <Plugin Root Directory>
make
```
Two file will be created inside dist folder. 
Copy the tar.gz file and upload in the mattermost plugin section.
