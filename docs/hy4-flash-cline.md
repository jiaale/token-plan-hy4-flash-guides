# Use Hy4 flash in Cline with Tencent Cloud Token Plan

Connect Cline to **Hy4 flash through Tencent Cloud TokenHub**, build a small browser-based app, and check how many plan credits the task uses.

This guide covers **Personal Token Plan on Tencent Cloud's international service**, using the Cline extension in VS Code. Pay-as-you-go keys use a different setup.

**[View TokenHub plans and pricing][tokenhub]** · **[Back to the README](../README.md)**

## Before you begin

You need:

- VS Code and the Cline extension.
- An active Personal Token Plan that includes Hy4 flash, with credits remaining.
- The dedicated API key for that plan.
- An empty local folder for your first task.

Token Plan is a paid subscription. TokenHub's free model token allocation is separate and cannot be used as plan credits. See the [official Token Plan FAQ](https://www.tencentcloud.com/document/product/1300/81318).

## 1. Get your Token Plan key

1. Open the [TokenHub product page][tokenhub], review the current plans, and choose the plan that fits your usage.
2. Complete the subscription through Tencent Cloud if you do not already have one.
3. In the Tencent Cloud console, open **TokenHub → Token Plan**.
4. Generate or copy the dedicated API key shown for your plan. Personal Token Plan keys typically begin with `sk-tp-`.

Use this key in Cline's provider settings. Keep it out of source files, Git commits, prompts, and screenshots.

The [official Token Plan Quick Start](https://www.tencentcloud.com/document/product/1300/81317) explains where to find the key and how to check plan usage.

## 2. Install and open Cline

1. In VS Code, open **Extensions** with `Ctrl+Shift+X` on Windows/Linux or `Cmd+Shift+X` on macOS.
2. Search for **Cline** and install the official extension. Use the [Cline installation guide](https://docs.cline.bot/getting-started/installing-cline) to verify the installation source.
3. Open your empty project folder in VS Code.
4. Open Cline from the sidebar, then open its settings.

You will use your TokenHub key as the model provider credential. This walkthrough does not use Cline's own model billing service.

## 3. Configure Hy4 flash

Enter these values in Cline's provider settings:

| Setting | Value |
| --- | --- |
| API Provider | `OpenAI Compatible` |
| Base URL | `https://tokenhub-intl.tencentcloudmaas.com/plan/v3` |
| API Key | Your dedicated Personal Token Plan key |
| Model ID / Model | `hy4-flash` |

Save the settings using the control available in your Cline version.

Three details matter:

- Select **OpenAI Compatible**, rather than the provider for a direct OpenAI account.
- Use the **plan** base URL above. Do not substitute the general TokenHub `/v1` address or append `/chat/completions` to this field.
- Use **`hy4-flash`**, not `hy4 flash`, `hy4`, or `hy4-preview`.

If you have enabled **Use different models for Plan and Act**, set the same TokenHub provider and `hy4-flash` model for both modes during this first test. Otherwise, switching modes may also switch your model provider.

Leave optional advanced settings at their defaults for the first text-only task. If your version requires custom model limits, check the current official specifications before changing them. A large context window is a capacity limit, not a reason to include an entire repository in every request.

Configuration references: [Tencent Cloud's Cline guide](https://www.tencentcloud.com/document/product/1300/81039), [Token Plan models and endpoints](https://www.tencentcloud.com/document/product/1300/81315), and [Cline's Plan & Act documentation](https://docs.cline.bot/core-workflows/plan-and-act).

## 4. Complete a first coding task

Start with a small task that you can inspect in a browser. A Pomodoro timer is useful because it exercises file creation, simple state management, and a few easy-to-check behaviors.

In **Plan mode**, paste:

```text
I want to build a small Pomodoro timer in this empty folder.

Use one index.html file with plain HTML, CSS, and JavaScript.
Do not add dependencies or external network requests.

Requirements:
- Default to a 25-minute session.
- Include a 1-minute option for testing.
- Provide Start, Pause, and Reset controls.
- Starting twice must not create two timers.
- Reset must stop the timer and restore the selected duration.
- At zero, stop and show a visible completion message.
- Make the page usable on a narrow mobile screen.

First explain your implementation plan and how I can check it.
Do not modify files yet.
```

Review the plan. Then switch to **Act mode** and ask:

```text
Implement the agreed plan in index.html.
Keep the code readable and explain how to open the page locally.
Tell me which checks you performed and which still need manual testing.
```

Review Cline's proposed file changes and approve the actions needed for the task. Open the resulting `index.html` file in a browser.

Check the result yourself:

| Check | Expected behavior |
| --- | --- |
| Start | The timer counts down |
| Pause | The displayed time stops changing |
| Reset | The timer stops and returns to the selected duration |
| Click Start repeatedly | The countdown does not accelerate |
| Run the 1-minute session | The timer stops at zero and shows completion |
| Narrow the browser window | The controls remain usable |

If something fails, describe the observed behavior to Cline and ask for a focused fix. Record the failure and retry rather than treating the first generated page as a verified success.

## 5. Check usage and decide whether to continue

Open **TokenHub → Token Plan** in the Tencent Cloud console and inspect the remaining credits and usage details. Use the console's plan records for billing; a client-side dollar estimate should not be treated as an invoice for a credit-based subscription.

For a useful first evaluation, record:

| Item | What to record |
| --- | --- |
| Setup | Cline version, operating system, model ID, and date |
| Outcome | Which manual checks passed or failed |
| Time | Time to a working result, including retries |
| Usage | Credits consumed for this task, separated from other activity |
| Follow-up | Whether you would use this setup for a similar task again |

One successful task is an initial usability check. To compare value, repeat a small set of representative tasks under consistent conditions and keep the failures as well as the successes.

When your plan credits are exhausted, calls stop until you upgrade or your next subscription cycle begins. Personal Token Plan does not automatically draw on pay-as-you-go billing or free model token allocations. See the [official FAQ](https://www.tencentcloud.com/document/product/1300/81318).

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| `401` / unauthorized | Check the `/plan/v3` base URL, the dedicated plan key, and the plan's status. A general TokenHub API key is not interchangeable with a plan key. |
| `20033` / invalid model | Check the spelling `hy4-flash` and confirm it appears in your plan's current model list. |
| `429` / rate limit exceeded | Pause before retrying and reduce simultaneous tasks. If it persists, inspect the usage details and contact support with the error information. |
| `20097` / monthly quota exhausted | Check remaining plan credits. Upgrade or wait for the next subscription cycle. |
| `20059` / input too long | Start a new task with less context and include only the files needed for the change. |
| It works in Plan mode but fails in Act mode | Check whether the two modes use different provider configurations. |

The numeric error codes above are documented in the [official Token Plan Quick Start](https://www.tencentcloud.com/document/product/1300/81317). For account-specific issues, use Tencent Cloud support. Never post your API key in a GitHub issue.

## Next steps

Try a focused change in a small existing project, such as adding a unit test or fixing a reproducible bug. Compare the time, retries, and credits required before expanding to larger workflows.

**[Review current TokenHub plans and pricing][tokenhub]**

---

**Documentation checked: November 16, 2026.** This revision has been reviewed against public setup documentation. A live end-to-end run in Cline has not yet been performed. Interface labels may vary by extension version.

This tutorial is maintained for TokenHub developer education and promotion. Product links include campaign attribution parameters.

[tokenhub]: https://www.tencentcloud.com/act/pro/tokenhub?lang=en&pg=&fromSource=intl.25875112.25875112.25875112&utm_medium=cpc&utm_id=intl.25875112.25875112.25875112
