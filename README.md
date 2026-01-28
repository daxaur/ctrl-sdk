# ctrl sdk

typescript sdk for ctrl platform. create workflows, monitor executions, manage session keys programmatically.

## installation

```bash
npm install @ctrl/sdk
```

## usage

### create a workflow

```typescript
import { CtrlClient } from '@ctrl/sdk'

const ctrl = new CtrlClient({
  apiKey: process.env.CTRL_API_KEY
})

const workflow = await ctrl.workflows.create({
  name: 'weekly eth dca',
  trigger: {
    type: 'cron',
    schedule: '0 0 * * 1'
  },
  actions: [
    {
      type: 'swap',
      tokenIn: 'USDC',
      tokenOut: 'ETH',
      amountIn: '100'
    }
  ]
})
```

### monitor executions

```typescript
const executions = await ctrl.executions.list(workflow.id)

executions.forEach(exec => {
  console.log(`${exec.status}: ${exec.transactionHash}`)
})
```

### manage session keys

```typescript
const sessionKey = await ctrl.sessionKeys.create({
  wallet: '0x...',
  expiresIn: '30d'
})

console.log('session key created:', sessionKey.id)
```

## features

- full typescript support
- type-safe workflow builder
- real-time execution monitoring
- session key management
- webhook integration
- rate limit handling

## api reference

full documentation: [docs.ctrl.app/sdk](https://docs.ctrl.app/sdk)

## examples

check `/examples` for complete workflows:
- dca strategies
- price alerts
- portfolio rebalancing
- take-profit automation

---

built for developers, by developers.
