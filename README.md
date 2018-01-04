# Searchable Flatlist

Wrapper component over Flatlist component to provide search functionality.

[![npm](https://img.shields.io/npm/v/searchable-flatlist.svg?style=plastic)](https://www.npmjs.com/package/searchable-flatlist) [![npm](https://img.shields.io/npm/dm/searchable-flatlist.svg?style=plastic)](https://npmjs.org/package/searchable-flatlist) [![npm](https://img.shields.io/npm/dt/searchable-flatlist.svg?style=plastic)](https://npmjs.org/package/searchable-flatlist)

## Preview

<img src="./gifs/search.gif" width="320" style="box-shadow: 4px 4px 50px #888888;"/>

## Usage

### Install from npm:

`npm install --save searchable-flatlist`

### Integrate into your app:

```js
import React, { Component } from "react";
import { StyleSheet, Text, View, TextInput } from "react-native";
import SearchableFlatlist from "searchable-flatlist";

const data = [
  { id: 1, name: "Francesco Raoux" },
  { id: 2, name: "Tasha Bonanno" },
  { id: 3, name: "Merle Braunstein" },
  { id: 4, name: "Aleda Bouzan" },
  { id: 5, name: "Issiah Elnaugh" }
];

export default class App extends Component {
  state = { searchTerm: "" };
  render() {
    let { sContainer, sSearchBar, sTextItem } = styles;
    return (
      <View style={sContainer}>
        <TextInput
          placeholder={"Search"}
          style={sSearchBar}
          onChangeText={searchTerm => this.setState({ searchTerm })}
        />
        <SearchableFlatlist
          searchProperty={"name"}
          searchTerm={this.state.searchTerm}
          data={data}
          containerStyle={{ flex: 1 }}
          renderItem={({ item }) => <Text style={sTextItem}>{item.name}</Text>}
          keyExtractor={item => item.id}
        />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  sContainer: {
    flex: 1,
    backgroundColor: "#F5FCFF"
  },
  sTextItem: {
    height: 50,
    width: "100%",
    textAlign: "center",
    textAlignVertical: "center",
    fontSize: 18
  },
  sSearchBar: {
    paddingHorizontal: 10,
    margin: 10,
    height: 50,
    borderColor: "gray",
    borderWidth: 1,
    fontSize: 18
  }
});
```

| Props            | Description                           | Value                                                                         | Required               |
| ---------------- | ------------------------------------- | ----------------------------------------------------------------------------- | ------------------------ |
| `data`           | data for flatlist                     | `object array`                                                                | :heavy_check_mark:       |
| `searchProperty` | property of the object to be searched | `string`                                                                      | :heavy_check_mark:       |
| `searchTerm`     | searching term                        | `string`                                                                      | :heavy_check_mark:       |
| `type`           | type of search                        | one of the following `SearchableFlatlist.WORDS` `SearchableFlatlist.INCLUDES` | :heavy_multiplication_x: |

`SearchableFlatlist.WORDS` - search words

`SearchableFlatlist.INCLUDES` - search everything (default)
