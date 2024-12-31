# Expo Linking.getInitialURL() Returns Null Inconsistently on Android

This repository demonstrates a bug in Expo's `Linking.getInitialURL()` API on Android.  The function intermittently returns `null` even when the app is launched via a deep link. This behavior is inconsistent and unreliable.

## Bug Description

The `Linking.getInitialURL()` method, intended to retrieve the URL used to launch the app, sometimes returns `null` on Android. This occurs despite the deep link successfully opening the application. The problem seems to be linked to the app's initialization process, particularly noticeable when launching from a cold start.

## Reproduction Steps

1. Clone this repository.
2. Run the app on an Android device or emulator.
3. Open a deep link that should trigger the `Linking.getInitialURL()` call.
4. Observe that `getInitialURL` may return `null`, leading to an unexpected app state.

## Solution

The provided solution attempts to mitigate this issue by adding a delay to ensure the app is fully initialized before calling `getInitialURL()`. Although this approach is not perfect, it helps improve the reliability of retrieving the initial URL in many cases.  Ideally, Expo should address the underlying timing issue within their Linking API.