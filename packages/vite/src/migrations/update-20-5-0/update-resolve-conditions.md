#### Update `resolve.conditions` to include defaults

The `resolve.conditions` option had previously had defaults provided by Vite. These defaults were `['module', 'browser', 'development|production']`.  
These defaults are no longer provided by Vite and must be explicitly included in the `resolve.conditions` option if used. However, it can be difficult to be sure immediately if you were using them or not, so this migration ensures they are added.

They can then be removed after some investigation.

Learn more: [https://vite.dev/guide/migration#default-value-for-resolve-conditions](https://vite.dev/guide/migration#default-value-for-resolve-conditions)

{% callout type="note" title="Remix" %}

Remix does not currently support Vite 6 and therefore any `vite.config` file for Remix will not be migrated.

{% /callout %}

#### Sample Code Changes

{% tabs %}
{% tab label="Before" %}

```{% fileName="vite.config.ts" %}
import { defineConfig } from 'vite';

export default defineConfig({
  resolve: {
    conditions: ['require'],
  },
  build: {
    outDir: 'dist',
  },
});
```

{% /tab %}
{% tab label="After" %}

```{% highlightLines=[4,5,6] fileName="vite.config.ts" %}
import { defineConfig } from 'vite';

export default defineConfig({
  resolve: {
    conditions: ['require', 'module', 'browser', 'development|production'],
  },
  build: {
    outDir: 'dist',
  },
});
```

{% /tab %}
{% /tabs %}
