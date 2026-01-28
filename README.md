# ctrl sdk

typescript sdk for ctrl platform. build workflows programmatically.

**status:** coming after launch. placeholder for now.

---

## planned api

```typescript
import { CtrlClient } from '@ctrl/sdk'

const ctrl = new CtrlClient({ apiKey: 'xxx' })

// create workflow
await ctrl.workflows.create({
  name: 'weekly dca',
  trigger: { type: 'cron', schedule: '0 0 * * 1' },
  actions: [{ type: 'swap', tokenIn: 'USDC', tokenOut: 'ETH', amount: '100' }]
})

// monitor executions
const logs = await ctrl.executions.list(workflowId)
```

---

## why?

web ui is great for most users. sdk for power users who want to:
- manage workflows from code
- integrate ctrl into their apps
- automate workflow creation
- monitor programmatically

---

## when?

month 1-2 after launch. need real users first.

---

building in public. follow progress: [@daxaur](https://x.com/daxaur)
