# Forta Bot Review Checklist

This document is intended to serve as a checklist for detection bot developers to ensure they are producing high quality bots. As a living, breathing document, if you feel there is something missing you are encouraged to create a PR 🙂

## Installation

- [ ] Run `npm install`
- [ ] Are `name` and `description` fields filled out correctly in package.json?
- [ ] Are there any libraries in package.json that are unused?
- [ ] Are development libraries correctly placed in the `devDependencies` section? i.e. testing libraries like jest or Typescript @types

## Documentation

- [ ] Is there a README.md?
- [ ] Does the README sufficiently describe what the bot does?
- [ ] Are alert descriptions provided for each type of alert?
- [ ] Are there any example transactions/blocks provided? If so, do they generate findings as expected?
- [ ] Does the code contain inline comments and is easy to follow?

## Testing

- [ ] Run `npm test`
- [ ] Are there unit tests? Do they pass? Do they take long to run (more than 5 seconds)?
- [ ] Are the tests making real network calls? Ideally these should be mocked out
- [ ] Are the tests covering the relevant code paths? i.e. both negative and positive test cases
- [ ] When the tests complete, does it complain about any memory leaks or other errors?

## Running

- [ ] Run `npm start`
- [ ] Does the bot actually run?
- [ ] Are there any errors thrown?
- [ ] Are there too many alerts being generated? i.e. every block or every other transaction

## Code

- [ ] Does the code do what the README claims its doing?
- [ ] Are there too many network calls being made? Could caching help?
- [ ] Can network calls be made concurrently to improve performance? i.e. using [`Promise.all`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) or [`ethers-multicall`](https://www.npmjs.com/package/ethers-multicall)
- [ ] Is the code split across an appropriate amount of files? Typically 1 alert per file
- [ ] Are the findings fields filled out correctly? Is there something missing that could be added? Is there too much information?
- [ ] Are the SDK methods being used appropriately? e.g. `filterLog`, `filterFunction`, `getEthersProvider`
- [ ] When reading event `args` from `filterLog`, does the argument actually exist in the event declaration?
- [ ] Does the bot follow [best practices](https://docs.forta.network/en/latest/best-practices/)?
- [ ] Does the bot handle failed network calls? Can it recover from these errors?
