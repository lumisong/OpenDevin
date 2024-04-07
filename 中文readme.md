<p align="center">
  <img alt="OpenDevin Logo" src="./logo.png" width="150" />
</p>

# OpenDevin: Code Less, Make More : 简化软件开发任务并提高创造效率

[demo-video.webm](https://github.com/OpenDevin/OpenDevin/assets/38853559/5b1092cc-3554-4357-a279-c2a2e9b352ad)

## Mission 任务🎯

Welcome to OpenDevin, an open-source project aiming to replicate [Devin](https://www.cognition-labs.com/introducing-devin), an autonomous AI software engineer who is capable of executing complex engineering tasks and collaborating actively with users on software development projects. This project aspires to replicate, enhance, and innovate upon Devin through the power of the open-source community.

OpenDevin，开源项目，复制 Devin，一个能够执行复杂工程任务并积极与用户在软件开发项目上合作的自主AI软件工程师。希望通过开源社区的力量复制、增强并创新 Devin。

## Work in Progress 进展🚧

OpenDevin is still a work in progress. But you can run the alpha version to see things working end-to-end.

OpenDevin仍在进行中。但是您可以运行alpha版本 `alpha version`，看到 `end-to-end` 端到端的工作。

### Requirements 要求

* Linux, Mac OS, or [WSL on Windows](https://learn.microsoft.com/en-us/windows/wsl/install)
* [Docker](https://docs.docker.com/engine/install/)
* [Python](https://www.python.org/downloads/) >= 3.11
* [NodeJS](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) >= 14.8

### Installation 安装

First, pull our latest sandbox image [here](https://github.com/opendevin/OpenDevin/pkgs/container/sandbox)

首先，`pull` 拉取我们 `latest` 最新的 `sandbox image` 沙箱镜像 [这里](https://github.com/opendevin/OpenDevin/pkgs/container/sandbox)

```bash
docker pull ghcr.io/opendevin/sandbox
```

Note: you need to be able to [run `docker` without sudo](https://docs.docker.com/engine/install/linux-postinstall/)

注意：您需要能够 [无需`sudo`运行`docker`](https://docs.docker.com/engine/install/linux-postinstall/)

Then copy `config.toml.template` to `config.toml`. Add an OpenAI API key to `config.toml`, or see below for how to use different models.

然后将 `config.toml.template` 复制到 `config.toml`。将OpenAI API密钥添加到 `config.toml`，或查看下面如何使用不同的模型。

```toml
LLM_API_KEY="sk-..."
```

Next, start the backend:

接下来，启动后端：

```bash
python -m pip install pipenv
python -m pipenv install -v
python -m pipenv shell
uvicorn opendevin.server.listen:app --port 3000
```

If `pipenv` doesn't work for you, you can also run:

如果 `pipenv` 对您不起作用，您也可以运行：

```bash
python -m pipenv requirements > requirements.txt && python -m pip install -r requirements.txt
```

Then, in a second terminal, start the frontend:

然后，在第二个终端中，启动前端：

```bash
cd frontend
npm install
npm start
```

You'll see OpenDevin running at localhost:3001

您将看到OpenDevin在localhost:3001上运行

1. 重点放在服务器端逻辑的 Python 和前端开发的 TypeScript 上。项目中大量使用 Python，前端使用 TypeScript。
2. 启动后台**：按照 README 中的说明使用 pipenv 启动后端。这包括安装依赖项和运行服务器。
3. 探索代码库**： 深入 Python 代码库，了解后端结构及其与前端的交互方式。特别注意服务器的设置及其处理请求的方式。

### Picking a Model 选择模型

We use LiteLLM, so you can run OpenDevin with any foundation model, including OpenAI, Claude, and Gemini.

我们使用LiteLLM，因此您可以使用任何基础模型运行OpenDevin，包括OpenAI、Claude和Gemini。

LiteLLM has a [full list of providers](https://docs.litellm.ai/docs/providers).

LiteLLM有一个[提供商完整列表](https://docs.litellm.ai/docs/providers)。

To change the model, set the `LLM_MODEL` and `LLM_API_KEY` in `config.toml`.

要更改模型，请在`config.toml`中设置`LLM_MODEL`和`LLM_API_KEY`。

For example, to run Claude:

例如，运行Claude：

```toml
LLM_API_KEY="your-api-key"
LLM_MODEL="claude-3-opus-20240229"
```

You can also set the base URL for local/custom models:

您还可以设置本地/自定义模型的基本URL：

```toml
LLM_BASE_URL="https://localhost:3000"
```

And you can customize which embeddings are used for the vector database storage:

您可以自定义用于向量数据库存储的嵌入：

```toml
LLM_EMBEDDING_MODEL="llama2" # can be "llama2", "openai", "azureopenai", or "local"
```

### Running on the Command Line 在命令行上运行

You can run OpenDevin from your command line:

您可以从命令行运行OpenDevin：

```bash
PYTHONPATH=`pwd` python opendevin/main.py -d ./workspace/ -i 100 -t "Write a bash script that prints 'hello world'"
```

## 🤔 What is [Devin](https://www.cognition-labs.com/introducing-devin)? Devin 是什么？

Devin represents a cutting-edge autonomous agent designed to navigate the complexities of software engineering. It leverages a combination of tools such as a shell, code editor, and web browser, showcasing the untapped potential of LLMs in software development. Our goal is to explore and expand upon Devin's capabilities, identifying both its strengths and areas for improvement, to guide the progress of open code models.

Devin代表了一种前沿的自主代理，旨在解决软件工程的复杂性。它利用了一系列工具，如shell、代码编辑器和Web浏览器，展示了LLM在软件开发中的潜力。我们的目标是探索和扩展Devin的能力，识别其优势和改进领域，以指导开放代码模型的进展。

## 🐚 Why OpenDevin? 为什么是 OpenDevin?

The OpenDevin project is born out of a desire to replicate, enhance, and innovate beyond the original Devin model. By engaging the open-source community, we aim to tackle the challenges faced by Code LLMs in practical scenarios, producing works that significantly contribute to the community and pave the way for future advancements.

OpenDevin项目的诞生源于复制、增强和创新原始Devin模型的愿望。通过吸引开源社区，我们旨在解决代码LLM在实际场景中面临的挑战，产生对社区有重大贡献的作品，并为未来的进步铺平道路。

## ⭐️ Research Strategy 研究策略

Achieving full replication of production-grade applications with LLMs is a complex endeavor. Our strategy involves:

1. **Core Technical Research:** Focusing on foundational research to understand and improve the technical aspects of code generation and handling.
2. **Specialist Abilities:** Enhancing the effectiveness of core components through data curation, training methods, and more.
3. **Task Planning:** Developing capabilities for bug detection, codebase management, and optimization.
4. **Evaluation:** Establishing comprehensive evaluation metrics to better understand and improve our models.

使用LLM实现`production-grade applications`生产级应用程序的`full replication`完全复制是一项复杂的工作`endeavor`。我们的策略`strategy`包括：

1. **核心技术研究:** 专注于基础研究，以`understand`了解和`improve`改进代码生成和处理`code generation and handling`的技术方面。
2. **专业能力:** 通过`data curation`数据整理、训练方法等手段提高`core components`核心组件的效果`Enhancing the effectiveness`。
3. **任务规划:** 开发用于`bug detection`错误检测、`codebase management`代码库管理和`optimization`优化的能力。
4. **评估:** 建立全面的评估指标，以更好地了解和改进我们的模型。

## 🛠 Technology Stack 技术栈

* **Sandboxing Environment:** Ensuring safe execution of code using technologies like Docker and Kubernetes.
* **Frontend Interface:** Developing user-friendly interfaces for monitoring progress and interacting with Devin, potentially leveraging frameworks like React or creating a VSCode plugin for a more integrated experience.

* **沙箱环境 `Sandboxing Environment`:** 使用Docker和Kubernetes等技术确保代码的安全执行`safe execution`。
* **前端界面 `Frontend Interface`:** 为`monitoring progress`监视进度和与Devin交互`interacting with Devin`开发用户友好的界面，可能利用React等框架或创建VSCode插件`plugin`以获得更一体化的体验`more integrated experience`。

Python、TypeScript 和 Docker。

* `OpenDevin` 使用 Docker 作为沙箱环境，请确保在系统中安装了 Docker。
* "docker pull ghcr.io/opendevin/sandbox "命令提取 OpenDevin 的最新沙箱映像
* 配置项目**： 将 `config.toml.template` 复制到 `config.toml` 并添加 OpenAI API 密钥。这一步对于本地运行项目至关重要。

## 🚀 Next Steps 下一步

An MVP demo is urgent for us. Here are the most important things to do:

* UI: a chat interface, a shell demonstrating commands, a browser, etc.
* Architecture: an agent framework with a stable backend, which can read, write and run simple commands
* Agent: capable of generating bash scripts, running tests, etc.
* Evaluation: a minimal evaluation pipeline that is consistent with Devin's evaluation.

一个MVP演示对我们来说是紧急的。以下是最重要的事情：

* UI：一个聊天界面`chat interface`，一个`shell demonstrating commands`演示命令的shell，一个`browser`浏览器等。
* 架构`Architecture`：一个`stable backend`稳定的后端代理框架`agent framework`，可以`read, write and run`读取、写入和运行简单的命令`simple commands`
* 代理`Agent`：能够生成bash脚本`scripts`、`running tests`运行测试等。
* 评估`Evaluation`：一个与Devin的评估`consistent`一致的最小评估管道`minimal evaluation pipeline`。

After finishing building the MVP, we will move towards research in different topics, including foundation models, specialist capabilities, evaluation, agent studies, etc.

完成构建MVP后，我们将朝着不同主题的研究方向前进，包括`foundation models`基础模型、`specialist capabilities`专业能力、`evaluation`评估、`agent studies`代理研究等。

## How to Contribute 如何贡献

OpenDevin is a community-driven project, and we welcome contributions from everyone. Whether you're a developer, a researcher, or simply enthusiastic about advancing the field of software engineering with AI, there are many ways to get involved:

* **Code Contributions:** Help us develop the core functionalities, frontend interface, or sandboxing solutions.
* **Research and Evaluation:** Contribute to our understanding of LLMs in software engineering, participate in evaluating the models, or suggest improvements.
* **Feedback and Testing:** Use the OpenDevin toolset, report bugs, suggest features, or provide feedback on usability.

For details, please check [this document](./CONTRIBUTING.md).

OpenDevin是一个社区驱动的项目`community-driven project`，我们欢迎每个人的贡献。无论您是`developer`开发人员、`researcher`研究人员，还是对通过AI推进软件工程领域感兴趣，都有许多参与的方式：

* **代码贡献:** 帮助我们开发核心功能`core functionalities`、`frontend interface`前端界面或`sandboxing solutions`沙箱解决方案。
* **研究和评估:** 为我们在软件工程中的LLM的理解做出贡献，参与评估模型，或提出改进建议。
* **反馈和测试:** 使用OpenDevin工具集`OpenDevin toolset`，报告错误`report bugs`，建议功能`suggest features`，或提供关于可用性的反馈`feedback on usability`。

有关详细信息，请查看[此文档](./CONTRIBUTING.md)。

## Join Us 加入我们

We use Slack to discuss. Feel free to fill in the [form](https://forms.gle/758d5p6Ve8r2nxxq6) if you would like to join the Slack organization of OpenDevin. We will reach out shortly if we feel you are a good fit to the current team!

我们使用Slack进行讨论。如果您想加入OpenDevin的Slack组织，请随时填写[表格](https://forms.gle/758d5p6Ve8r2nxxq6)。如果我们认为您适合当前团队，我们将很快与您联系！

Stay updated on OpenDevin's progress, share your ideas, and collaborate with fellow enthusiasts and experts. Together, we can make significant strides towards simplifying software engineering tasks and creating more efficient, powerful tools for developers everywhere.

随时了解OpenDevin的进展，分享您的想法，并与其他爱好者和专家合作。我们可以共同朝着简化软件工程任务并为全球开发人员创造更高效、更强大的工具迈出重要的一步。
