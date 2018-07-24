# Contributions

## Accept Functions for Popover Anchor
[PR 10420](https://github.com/mui-org/material-ui/pull/10420) resolves [Issue 10411](https://github.com/mui-org/material-ui/issues/10411) by allowing a function to return the Popover anchor.

It is unnecessary to require the Popover (and its parent) to re-render whenever the anchor changes. By passing an unchanging function reference that returns a changing anchor, the Popover can always anchor to the correct element without having to re-render as that element changes.

## Cache Classes
[PR 11202](https://github.com/mui-org/material-ui/pull/11202) resolves [Issue 11158](https://github.com/mui-org/material-ui/issues/11158) by caching the `classes` prop created by the `withStyles` Higher Order Component.

Previously, the `withStyles` HOC would create the classes prop as a new object during every render. This would cause the wrapped component to re-render even if no props or key-value pairs changed, due to the new object reference being passed.

By caching the object reference and only changing it when key-value pairs change, the wrapped component does not re-render unnecessarily, boosting performance.
