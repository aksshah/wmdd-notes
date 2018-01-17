# stdlib notes

using local node_modules

add the following function to your bashrc

```bash
npm-do() {
  (PATH=$(npm bin):$PATH; eval $@;)
}
```
