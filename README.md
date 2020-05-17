## svelte-data-table

A simple but powerful data table in svelte.

## Usage

### Config

```js
export const config = {
  no: {
    name: "name", // head column
    type: "number", // number, string -> will align in different way
    formatter: (t) => `#${t}`, // how to format data
    hideMobile: true, // hide in mobile (will deprecate probably)
  },
  name: {
    name: "FISH",
    type: "text",
    align: "left", // text align
    className: "fishName", // custom class name
  },
  price: {
    name: "價格",
    sortable: true, // sortable in table head
    formatter: function priceFormatter(t) {
      return formatNumber(t);
    },
    comparator: priceComparator, // when sortable is ture, comparator is required.
  },
  price08: {
    accessor: (d) => d.price, // a function to define how to get data in this column
  },
};
```

## TODOs

- [ ] pagination support
- [ ] Fixed header
- [ ] sortable
- [ ] slot
- [ ] expanded view
- [ ] group
- [ ] row and column event handler
- [ ] selectable
- [ ] Event communication
- [ ] a11y support
- [ ] test
