# [Svelte crash course by The Net Ninja](https://www.youtube.com/watch?v=lnpdn2rE2N8)

In case of using not **yarn** package manager, change params in `rollup.config.js` at line 20.

```javascript
  return {
    writeBundle() {
      if (server) return;
      server = require('child_process').spawn(
        'yarn',
        ['start', '--', '--dev'],
        {
          stdio: ['ignore', 'inherit', 'inherit'],
          shell: true,
        }
      );
```
