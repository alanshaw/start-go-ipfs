# start-go-ipfs

> Spawn a go-ipfs daemon from Node.js

## Install

```sh
npm i start-go-ipfs
```

## Usage

First install your favourite go-ipfs daemon, you could `npm install go-ipfs-dep`, `brew install ipfs` or whatever.

```js
const startDaemon = require('start-go-ipfs')

const daemon = await startDaemon({
  // The path to your IPFS executable.
  // default: node_modules/go-ipfs-dep/go-ipfs/ipfs (required if go-ipfs-dep not installed)
  execPath: '/usr/local/bin/ipfs',
  // Path to your IPFS repo (default shown)
  ipfsPath: '~/.ipfs',
  // Config to merge with your current config at ~/.ipfs/config (optional)
  config: { /* IPFS config */ },
  // Options for deepmerge (defaults shown)
  // see https://www.npmjs.com/package/deepmerge#arraymerge
  mergeOptions: {
    arrayMerge: function overwrite (_, sourceArray) { return sourceArray }
  },
  // Pipe stdout and stderr to these writeable streams if provided
  stdout: process.stdout,
  stderr: process.stderr
})

// Your go IPFS Daemon is now READY to use

// Your daemon configuration
console.log(daemon.config)

// Node.js child process
// https://nodejs.org/api/child_process.html#child_process_class_childprocess
// ...enhanced by execa
// https://www.npmjs.com/package/execa
await daemon.process
```

## Contribute

Feel free to dive in! [Open an issue](https://github.com/alanshaw/start-go-ipfs/issues/new) or submit PRs.

## License

[MIT](LICENSE) © Alan Shaw
