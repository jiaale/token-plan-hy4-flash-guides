# Tencent Cloud TokenHub: Hy4 flash & Cline Guides

Practical guides for using **Hy4 flash through Tencent Cloud TokenHub** in your everyday coding workflow. Start with Cline, complete a small task, and check your usage before moving to a larger project.

**[View TokenHub plans and pricing][tokenhub]** · **[Set up Hy4 flash in Cline](docs/hy4-flash-cline.md)**

## What is TokenHub?

Tencent Cloud TokenHub provides access to Tencent Hunyuan and supported third-party models through compatible interfaces. **Hy4 flash is a model available through TokenHub; Token Plan is a subscription option for supported AI tools.**

Choose the access option that fits your work:

| Your workflow | Access option | Where to start |
| --- | --- | --- |
| Use a supported AI coding tool such as Cline | Personal Token Plan, with a dedicated plan key and monthly credits | [Hy4 flash + Cline guide](docs/hy4-flash-cline.md) |
| Add model calls to your own application or backend | TokenHub pay-as-you-go API access | [Explore TokenHub][tokenhub] and consult the [Language Model API Overview](https://www.tencentcloud.com/document/product/1300/80632) |

Personal Token Plan and pay-as-you-go access have different keys, endpoints, and billing rules. The Cline tutorial in this repository covers **Personal Token Plan on Tencent Cloud's international service**.

## Why start with Hy4 flash?

Hy4 flash is positioned as a cost-effective model for everyday coding assistance, agent workflows, and document or chart understanding. Its advertised capabilities include a **1M-token context window** and **image understanding**. See the [current product information][tokenhub] for availability and pricing.

Useful tasks to try include:

- Building a small browser-based utility from a clear specification.
- Explaining unfamiliar code and making a focused change.
- Adding tests or investigating a bug in a small project.
- Discussing a screenshot when image input is enabled in your client.

Start with a task whose result you can inspect. A model's context limit or feature list does not, by itself, establish how well it will complete your particular task.

## Quick configuration: Hy4 flash in Cline

After purchasing an eligible Personal Token Plan and obtaining its dedicated API key, configure Cline as follows:

| Cline setting | Value |
| --- | --- |
| API Provider | `OpenAI Compatible` |
| Base URL | `https://tokenhub-intl.tencentcloudmaas.com/plan/v3` |
| API Key | Your dedicated Token Plan key, typically beginning with `sk-tp-` |
| Model ID | `hy4-flash` |

Use the exact model ID, including the hyphen. Enter the base URL as shown; do not append `/chat/completions` to Cline's Base URL field.

**[Follow the complete Cline tutorial](docs/hy4-flash-cline.md)** for installation, a first task, usage checks, and troubleshooting. The settings follow Tencent Cloud's [Cline integration guide](https://www.tencentcloud.com/document/product/1300/81039) and [Token Plan model list](https://www.tencentcloud.com/document/product/1300/81315).

## Understand what you are buying

- **Personal Token Plan:** a subscription with monthly credits for supported AI tools. It is not an unrestricted API subscription for custom backends or non-interactive batch scripts.
- **Free model tokens:** separate from Personal Token Plan credits. A free trial allocation does not fund the plan.
- **When plan credits run out:** upgrade or wait for the next subscription cycle. The plan does not automatically switch to pay-as-you-go billing.
- **Prices and promotions:** check the current offer and checkout details before buying; this repository does not maintain a separate price list.

Sources: [Token Plan Overview](https://www.tencentcloud.com/document/product/1300/81315) and [Token Plan FAQs](https://www.tencentcloud.com/document/product/1300/81318).

**[Compare current plans and get started with TokenHub][tokenhub]**

## Documentation and feedback

| Resource | Purpose |
| --- | --- |
| [Hy4 flash in Cline](docs/hy4-flash-cline.md) | Step-by-step setup and a first coding task |
| [Official Token Plan Quick Start](https://www.tencentcloud.com/document/product/1300/81317) | Key management, usage details, and error codes |
| [Official Cline provider setup](https://docs.cline.bot/provider-config/openai-compatible) | How Cline configures a compatible model provider |

If a step is unclear, open an issue with your Cline version, operating system, and the error message. Remove API keys and other sensitive information from screenshots or logs. Account and billing issues should go through Tencent Cloud support.

## About this repository

Maintained on a personal GitHub account for TokenHub developer education and promotion. This repository is not an official Tencent Cloud support channel. Product links contain campaign attribution parameters.

**Documentation checked: November 16, 2026.** These guides are based on public product documentation. A live end-to-end Cline test has not yet been completed for this revision; no benchmark or cost-saving results are claimed.

[tokenhub]: https://www.tencentcloud.com/act/pro/tokenhub?lang=en&pg=&fromSource=intl.25875112.25875112.25875112&utm_medium=cpc&utm_id=intl.25875112.25875112.25875112
