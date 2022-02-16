# NFT Collection Creation 

![nft_pic](https://user-images.githubusercontent.com/78571802/154198732-8838709e-fabf-4d81-b23d-cf752b99f677.jpeg)

## The source code for nft creation:
``` sh
https://github.com/HashLips/hashlips_art_engine/blob/main/src/config.js
```

## The latest version of node installed:
``` sh
node -v  # To check node js version
v16.14.0 # version installed
```

## Layers Created:
The different layers were created and named as folders in the 'layers' directory. All the layer assets were included in these directories. The assets were named with a rarity weight attached in the file name like so: `greenn_bg#10.png`. Where the variable, `rarityDelimiter`, is denoted by the delimiter `#`

The layer assets labeled with `#10` (for regular), `#5` (for rare assets), and `#2` (for super rare).

## Layers added:
``` sh
- Backgrounds
- Faces
- Glasses
- Hats
```

## Layer Configurations
Multiple different `layerConfigurations` were added to the collection. 
```js
const layerConfigurations = [
  {
    // Creates up to 60 artworks
    growEditionSizeTo: 60,
    layersOrder: [
      { name: "Backgrounds" },
      { name: "Faces" },
      { name: "Glasses" },
      { name: "Hats" },
    ],
  },
  {
    // Creates an additional 20 artworks with hats omitted
    growEditionSizeTo: 80,
    layersOrder: [
      { name: "Backgrounds" },
      { name: "Faces" },
      { name: "Glasses" },
    ],
  },
  {
    // Creates an additional 20 artworks with glasses omitted
    growEditionSizeTo: 100,
    layersOrder: [
      { name: "Backgrounds" },
      { name: "Faces" },
      { name: "Hats" },
    ],
  },
];
```
We mixed up the `layerConfigurations` order on how the images are saved by setting the variable `shuffleLayerConfigurations` in the `config.js` file to true. 

## Build
The images to be created were outputted to the `build/images` directory and the json in the `build/json` directory:

```sh
node index.js
```

The program will output all the images in the `build/images` directory along with the metadata files in the `build/json` directory. Each collection will have a `_metadata.json` file that consists of all the metadata in the collection inside the `build/json` directory. The `build/json` folder also will contain all the single json files that represent each image file. The single json file of a image looks like this:

```json
{
  "name": "Cryptobaras #1",
  "description": "To Be Or Not To Be Cryptobara",
  "image": "ipfs://QmXwnf99NoKwVvKpJ5WnrEmbbqtpEarJqF6jUXUzmkSZhk/1.png",
  "dna": "a350a741f5ee6e5a6242ff9fe1e360faa3672d7f",
  "edition": 1,
  "date": 1644770031593,
  "attributes": [
    {
      "trait_type": "Backgrounds",
      "value": "yellow_bg"
    },
    {
      "trait_type": "Faces",
      "value": "moss_capy"
    },
    {
      "trait_type": "Glasses",
      "value": "blue_shades"
    },
    {
      "trait_type": "Hats",
      "value": "pink_sun_hat"
    }
  ],
  "compiler": "HashLips Art Engine"
}
```
## General Metadata
```js
// General metadata for Ethereum
const namePrefix = "CryptoBara_TestRun";
const description = "To Be Or Not To Be A CryptoBara";
const baseUri = "ipfs://QmXwnf99NoKwVvKpJ5WnrEmbbqtpEarJqF6jUXUzmkSZhk"
```

### Generate a preview image
Create a preview image collage of your collection, run:
```sh
npm run preview
```
![preview](https://user-images.githubusercontent.com/78571802/154199679-34e9871f-6900-412f-92fd-c5c13633b6b8.png)


### Generate GIF images from collection

In order to export gifs based on the layers created, we set the export on the `gif` object in the `src/config.js` file to `true`. 
Setting the `repeat: -1` will produces a one time render and `repeat: 0` produces loop forever.
```js
const gif = {
  export: true,
  repeat: 0,
  quality: 100,
  delay: 500,
};
```
![preview](https://user-images.githubusercontent.com/78571802/154199809-dd13384c-8ae4-4c1f-a687-fa89d9217263.gif)


### Printing rarity data (Experimental feature)

To see the percentages of each attribute across the collection, run:
```sh
npm run rarity
```

The output will look something like this:

```sh
Trait type: Backgrounds
{
  trait: 'cyan_bg',
  weight: '10',
  occurrence: '11 in 100 editions (11.00 %)'
}
{
  trait: 'green_bg',
  weight: '10',
  occurrence: '15 in 100 editions (15.00 %)'
}
{
  trait: 'grey_bg',
  weight: '10',
  occurrence: '19 in 100 editions (19.00 %)'
}
{
  trait: 'orange_bg',
  weight: '10',
  occurrence: '21 in 100 editions (21.00 %)'
}
{
  trait: 'pink_bg',
  weight: '10',
  occurrence: '20 in 100 editions (20.00 %)'
}
{
  trait: 'yellow_bg',
  weight: '10',
  occurrence: '14 in 100 editions (14.00 %)'
}
```
The images folder was uploaded to ![pinata](https://user-images.githubusercontent.com/78571802/154200040-ed70f0aa-9aad-4c77-99d2-7e4a721f9f23.png)
![Screen Shot 2022-02-16 at 12 13 20 AM](https://user-images.githubusercontent.com/78571802/154200646-e71212bf-0639-4138-bba1-be1ced303e24.png)

## Contract on Rinkeby Network
![Screen Shot 2022-02-16 at 12 21 00 AM](https://user-images.githubusercontent.com/78571802/154201646-77b48027-2d23-42cb-a850-d87abcc71676.png)

## Minted Collection on Etherscan Testnet
![Screen Shot 2022-02-16 at 12 22 55 AM](https://user-images.githubusercontent.com/78571802/154201705-7686d1d3-f17a-4c64-b833-7d8ec0bc7215.png)


