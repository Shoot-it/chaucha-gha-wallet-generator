# Chaucha Wallet Generator Action

This is a simple https://chaucha.cl wallet generator
for usage within Github actions.

## Usage

### Example workflow

```yaml
name: Integration Test
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Self test
        id: selftest

        # Put your action repo here
        uses: proyecto-chaucha/chaucha-gha-wallet-generator@master
        with:
          value: "test"

      - name: Check outputs
        run: |
          test "${{ steps.selftest.outputs.privkey }}" == "8G63zuGKfQ7ho4X1ytHr75HmrZxJq3NFQ51YSPdyDh4hsHEr2Bg"
          test "${{ steps.selftest.outputs.pubkey }}" == "ch4uy1bAfLLf6RMcmkrHBa8oxtuMTgwXyS"
```

### Inputs

| Input                | Description                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------- |
| `value` _(optional)_ | String value to create a new wallet address. Empty value will generate a random address. |

### Outputs

| Output    | Description                        |
| --------- | ---------------------------------- |
| `privkey` | Chaucha Wallet Private Key Address |
| `pubkey`  | Chaucha Wallet Public Key Address  |
