# React 19 useTransition Hook Blocking Main Thread Bug

This repository demonstrates a bug in React 19's `useTransition` hook where a long-running transition function can block the main thread, resulting in UI freezes and React.StrictMode warnings.  The solution involves using `startTransition` more effectively and potentially implementing workarounds for long running tasks.

## Bug Description:
The `useTransition` hook, when provided with an expensive transition function, can cause performance issues. This is because React executes the transition function synchronously by default. If this function is slow, React's UI update is delayed causing the UI to become unresponsive.

## Solution:
The solution is to ensure your transition function is asynchronous and not blocking the UI thread. This is typically done by using `setTimeout`, `Promise`, or other asynchronous methods to offload the heavy lifting to a Web Worker, for example.