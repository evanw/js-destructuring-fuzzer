# JavaScript Destructuring Fuzzer

This is a fuzzer that generates test cases for destructuring assignment and uses them to verify the correctness of JavaScript transpilers that rewrite the transforms to older JavaScript. It's currently configured to test transforming JavaScript to ES6, which involves rewriting object rest patterns (e.g. `let {...x} = y`).

This fuzzer tests three transpilers: [esbuild](https://github.com/evanw/esbuild), [TypeScript](https://github.com/microsoft/TypeScript), and [Babel](https://github.com/babel/babel). Each test checks that the transpiled code behaves the same as running the original code natively. The only transpiler that passes all tests is esbuild. Both TypeScript and Babel have various destructuring correctness bugs.

## Usage

Download this code, run `npm ci`, then run `node destructuring-fuzzer.js`. This will print out a chart with various test cases and if they passed or failed. See [sample-output.txt](./sample-output.txt) for example output.

Pass the `--verbose` flag to see the input code and the generated output for failed test cases. This will likely generate a lot of terminal output.
