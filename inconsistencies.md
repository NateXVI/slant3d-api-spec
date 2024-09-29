# API Inconsistencies

## `orderId` Type

When placing an order, the API returns the order ID as a string, but when listing orders it returns it as a number. These two types should be the same.

## Tracking Path

The tracking apth (`/api/order/{orderId}/get-tracking`) is the only path that has a verb. Usually paths don't have verbs, especially paths that are used to `GET` data, because the method is used to describe the action that is being performed. This path could be changed to `/api/order/{orderId}`, `/api/order/{orderId}/tracking` or `/api/tracking/{orderId}` to make it more consistent with the other paths.

## No 404 Errors

When entering an invalid order ID to the canel order path, a 400 error is returned, but a 404 error should be returned instead because the order does not exist.

When an invalid order ID is entered to the get tracking path, a 200 status is returned with an object containing the property `trackingNumbers` that is null. A 404 error should be returned instead because the order does not exist.
