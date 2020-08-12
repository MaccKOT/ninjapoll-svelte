# NinjaPoll Tutorial Project

## [Svelte crash course by The Net Ninja](https://www.youtube.com/watch?v=f0v5WcrU_vM)

In case of using not **yarn** package manager, change params in `rollup.config.js` at the line 20.

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
