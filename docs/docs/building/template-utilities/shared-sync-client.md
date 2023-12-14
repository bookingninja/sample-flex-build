---
title: Shared Sync client
---

Location: `flex-template-astrawatt-flex-build/src/utils/sdk-clients/sync/SyncClient.ts`

A common plugin usage pattern is temporarily storing data in [Twilio Sync](https://www.twilio.com/docs/sync). Sync is a product included in the Flex subscription that allows synchronization of real-time updates across various clients. For example, the supervisor-barge-coach feature uses Sync to maintain monitoring/coaching state across clients for display/alerting purposes. While Flex UI provides a limited Sync client in the form of the Insights client, plugins must instantiate their own Sync client in order to use Sync. When multiple plugins use Sync, this results in multiple Sync clients. Sync has [limits on the number and rate of connections](https://www.twilio.com/docs/sync/limits), which are low enough that large contact centers cannot afford to have more than one active Sync client per Flex UI instance.

The template solves this problem by instantiating a single shared Sync client, which all features are able to use. The default export of the `SyncClient` module provides direct access to this shared client.

For examples of how to use the shared Sync client, see the following features:

- **park-interaction**: `flex-template-astrawatt-flex-build/src/feature-library/park-interaction/utils/SyncHelper.js`
- **supervisor-barge-coach**: `flex-template-astrawatt-flex-build/src/feature-library/supervisor-barge-coach/utils/sync/Sync.ts`
