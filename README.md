# React useEffect setInterval Memory Leak

This repository demonstrates a common error in React applications: memory leaks caused by the improper use of `setInterval` within the `useEffect` hook.  The example shows a component that increments a counter every second. However, because the `setInterval` function is not properly cleaned up when the component unmounts, it continues to run, consuming resources even after the component is no longer needed. This can lead to memory leaks and performance degradation, especially in applications with many such components.

## How to Reproduce

1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm start` to start the development server.
4. Observe the counter incrementing in the browser.
5. Navigate away from the page or refresh the browser.  The `setInterval` function continues to run, which can be verified via browser developer tools.

## Solution

The solution involves using the return value of `useEffect` to provide a cleanup function that stops the interval when the component unmounts.

## Learning Points

* Always clean up resources within `useEffect` hooks, especially those that create long-running processes, like `setInterval` or `setTimeout`.
* Use the return value of `useEffect` to provide a cleanup function that runs when the component unmounts or when the effect's dependencies change.
* Understanding the lifecycle of React components is crucial for preventing memory leaks and creating efficient applications.