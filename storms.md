## Commit: feat(core): bootstrap runtime configuration and feature registry

```
stormsagents/
├── src/
│   ├── config/
│   │   ├── app.ts
│   │   ├── env.ts
│   │   ├── providers.ts
│   │   └── features.ts
│   ├── core/
│   │   ├── agent.ts
│   │   ├── runtime.ts
│   │   ├── registry.ts
│   │   └── types.ts
│   └── constants/
│       └── metadata.ts
```

### src/config/app.ts

```ts
export const AppConfig = {
  name: "Storms Agents",
  website: "https://stormsagents.fun",
  repository: "stormsagents",

  version: "0.1.0",

  runtime: {
    defaultProvider: "openai",
    timeout: 30000,
    maxConcurrency: 10,
    telemetry: true,
    persistentMemory: true,
  },

  ui: {
    theme: "system",
    animations: true,
    sidebarCollapsed: false,
  },
};
```

### src/config/features.ts

```ts
export const FeatureFlags = {
  authentication: true,
  persistentMemory: true,
  multiModel: true,
  apiKeys: true,
  browserExtension: true,
  weatherFeeds: true,
  whaleAlerts: true,
  auditLogs: true,

  experimental: {
    coordinator: true,
    agentMarketplace: false,
    pluginSDK: false,
    workflows: true,
    realtimeEvents: true,
  },
};
```

### src/config/providers.ts

```ts
export const SupportedProviders = [
  {
    id: "openai",
    enabled: true,
    models: ["gpt-5", "gpt-4.1"],
  },
  {
    id: "anthropic",
    enabled: true,
    models: ["claude-opus-4", "claude-sonnet-4"],
  },
  {
    id: "google",
    enabled: true,
    models: ["gemini-2.5-pro"],
  },
  {
    id: "xai",
    enabled: true,
    models: ["grok-4"],
  },
];
```

### src/core/types.ts

```ts
export interface AgentRuntime {
  id: string;
  provider: string;
  model: string;

  memoryEnabled: boolean;
  toolsEnabled: boolean;

  createdAt: Date;
  updatedAt: Date;
}
```

### Commit message

```
feat(core): bootstrap runtime configuration

- add centralized runtime configuration
- create feature flag registry
- register model provider definitions
- initialize shared agent runtime types
- prepare foundation for workflow engine
```
