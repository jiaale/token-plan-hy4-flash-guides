# Use Hy4 flash with Tencent Cloud Token Plan

Use **Hy4 flash with a Tencent Cloud Personal Token Plan** in supported AI tools. This repository helps you choose a subscription, connect your coding tool, and check the credits used by a small task. The first walkthrough uses Cline in VS Code.

**[Compare Token Plan subscriptions][tokenplan]** · **[Set up Hy4 flash in Cline](docs/hy4-flash-cline.md)**

## What you are subscribing to

**Personal Token Plan** is Tencent Cloud's paid subscription for supported AI tools, with monthly credits and a dedicated plan key. It is available through **TokenHub**, Tencent Cloud's model service platform.

| Name | Role in this guide |
| --- | --- |
| **Token Plan** | The subscription you purchase and use in a supported tool |
| **Hy4 flash** | The model selected for the coding walkthrough, with model ID `hy4-flash` |
| **TokenHub** | The Tencent Cloud platform where you manage the plan, key, and usage |

A plan provides access to its currently supported models, so you can switch models within the subscription. Model availability and credit deduction rates may change; check the [official Token Plan overview](https://www.tencentcloud.com/document/product/1300/81315) and your console before starting.

## Start with a Token Plan

1. **[Compare Lite, Standard, Pro, and Max][tokenplan].** Review the monthly credits, supported tools, and current checkout price.
2. **Subscribe to a Personal Token Plan** that fits your expected usage. If you already have an active plan, check its remaining credits.
3. **Get the dedicated plan key** from **TokenHub → Token Plan** in the Tencent Cloud console.
4. **[Connect Hy4 flash in Cline](docs/hy4-flash-cline.md)**, complete a small coding task, and review the plan credits consumed.

The subscription covers model usage through supported tools. Cline is the coding tool used in this walkthrough; you install and configure it separately.

## Why try Hy4 flash?

Hy4 flash is the featured model in this guide. Tencent Cloud lists a **1M-token context window**, **image understanding**, **function calling**, and **structured output** among its capabilities. See the [official model specifications](https://www.tencentcloud.com/document/product/1300/78934).

Start with a task whose result you can inspect:

- Build a small browser-based utility from a clear specification.
- Explain unfamiliar code and make a focused change.
- Add a test or investigate a reproducible bug.

The tutorial includes a Pomodoro timer task with concrete acceptance checks. Record the result, repair attempts, and credits used to evaluate whether the setup fits your work.

## Quick configuration: Hy4 flash in Cline

After subscribing and obtaining your dedicated Personal Token Plan key:

| Cline setting | Value |
| --- | --- |
| API Provider | `OpenAI Compatible` |
| Base URL | `https://tokenhub-intl.tencentcloudmaas.com/plan/v3` |
| API Key | Your dedicated Token Plan key, typically beginning with `sk-tp-` |
| Model ID | `hy4-flash` |

Enter the base URL exactly as shown. Do not append `/chat/completions`. If you use separate Plan and Act configurations in Cline, configure the same provider and model in both for your first task.

**[Follow the complete Hy4 flash coding setup tutorial](docs/hy4-flash-cline.md)** for installation, configuration, a first task, usage checks, and troubleshooting.

Configuration sources: [Tencent Cloud's Cline guide](https://www.tencentcloud.com/document/product/1300/81039) and [Token Plan models and endpoints](https://www.tencentcloud.com/document/product/1300/81315).

## Check the plan terms before subscribing

- **Monthly credits:** usage is deducted according to the selected model and its applicable credit rates. Unused monthly credits do not carry over.
- **Supported tools:** Personal Token Plan is for eligible AI tools. Its key must not be used for custom application backends or non-interactive batch scripts.
- **Free model tokens:** TokenHub's separate free model allocation does not fund Token Plan credits.
- **Exhausted credits:** requests stop when the allowance is exhausted. The plan does not automatically switch to pay-as-you-go billing; check the available upgrade or next-cycle options.
- **Prices and promotions:** use the current subscription and checkout terms. Per-million-token API prices are a separate billing option, not the price of a Token Plan subscription.

Sources: [Token Plan Overview](https://www.tencentcloud.com/document/product/1300/81315) and [Token Plan FAQs](https://www.tencentcloud.com/document/product/1300/81318).

**[Choose a Token Plan for Hy4 flash][tokenplan]**

## Need model access for your own application?

TokenHub also offers separate pay-as-you-go API access for applications and backends. That route has different credentials, endpoints, and billing rules. See the [Language Model API Overview](https://www.tencentcloud.com/document/product/1300/80632). This repository's Cline walkthrough uses Personal Token Plan.

## Documentation and feedback

| Resource | Purpose |
| --- | --- |
| [Hy4 flash coding setup with Token Plan](docs/hy4-flash-cline.md) | Step-by-step Cline setup and a first coding task |
| [Official Token Plan Quick Start](https://www.tencentcloud.com/document/product/1300/81317) | Key management, usage details, and error codes |
| [Official Cline provider setup](https://docs.cline.bot/provider-config/openai-compatible) | Compatible model provider settings |

If a step is unclear, open an issue with your Cline version, operating system, and a redacted error message. Account and billing issues should go through Tencent Cloud support.

## About this repository

Maintained on a personal GitHub account for Tencent Cloud Token Plan developer education and promotion. TokenHub provides the underlying platform. This repository is not an official Tencent Cloud support channel. Product links contain campaign attribution parameters.

**Documentation checked: November 16, 2026.** These guides are based on public product documentation. A live end-to-end Cline test has not yet been completed for this revision; no benchmark or cost-saving results are claimed.

[tokenplan]: https://www.tencentcloud.com/act/pro/tokenhub?lang=en&pg=&fromSource=intl.25875112.25875112.25875112&utm_medium=cpc&utm_id=intl.25875112.25875112.25875112
