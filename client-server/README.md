# mpc-hello (client <> server)

This is a template repository designed to be the hello-world of
[mpc-framework](https://github.com/voltrevo/mpc-framework).

It uses [summon](https://github.com/voltrevo/summon) for circuit generation
and [emp-wasm-backend](https://github.com/voltrevo/emp-wasm-backend) for
secure 2PC.

It's a minimal web app where users can make 1-to-1 connections with a server
and compute the larger of two numbers.

- 250 sloc
- Simple frontend
- Communication with WebSocket
- Circuit code included via ordinary project files

Below are other examples of mpc-hello applications you may want to explore:

- [**Client-Client**](../client-client)
- [**Server-Server**](../server-server)
- [**MPC-Hello with Next.js**](../server-server)

## Running Locally

```sh
npm install
npm run host
npm run join
```

## Updating the Percentage Display

The percentage display works using a constant `TOTAL_BYTES` and comparing this to the number of
bytes sent and received:
```ts
const TOTAL_BYTES = 248476;
```

When you change the circuit, this number needs to be changed to calculate the correct percentages.
To do this, add a log when `currentBytes` is updated:

```ts
currentBytes += msg.byteLength;                     // Note: there are two of these
console.log('Total bytes exchanged', currentBytes); // Add this line in both places
```

Run your app, note the highest value logged, and update `TOTAL_BYTES` to this value.

## License

This is a template repository. You are free to use it as a starting point for
your own work without restriction. You may modify it, distribute it, and apply
your own licensing terms to your derived work as you see fit. This software is
provided "AS IS" without warranty of any kind, as described by the MIT license.
