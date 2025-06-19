## Remove `$fragmentRefs` from generated code

```typescript
const config: CodegenConfig = {
  ...
  generates: {
    './gql/': {
      preset: 'client',
      plugins: [],
      presetConfig: {
        fragmentMasking: false // HERE
      }
    }
  }
}
```