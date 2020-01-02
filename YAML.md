## YAML Fundamnetals

- YAML files are composed of maps and lists
- Indentation matters (be consistent!)
- Always use spaces
- Maps:
  - name: value pairs
  - Maps can contain other Maps for more complex data structures
- Lists:
  - Sequence of items
  - Multiple maps can be defined in a list

## Example of YAML file:
```yaml
key: value
complexMap:
  key1: value1
  key2:
    subKey: value
items:
  - item1
  - item2
itemsMap:
  - map1: value
    map1Prop: value
  - map2: value
    map2Prop: value
```
- YAML maps define a key and value
- More complicated map structures can be defined using a key that references another map
- YAML lists can be used to define a sequence of items
- YAML lists can define a sequence maps
