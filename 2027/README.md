# REST League 2027

Welcome to **REST League 2027**, the 2<sup>nd</sup> edition of the ultimate competition for automated **black-box testing** tools designed for **RESTful APIs**.

> 🎖️ Accepted to the [ICSE2027](https://conf.researchr.org/home/icse-2027) Competition Track 🎖️

The goal of REST League is to evaluate the performance of open-source and proprietary tools in finding bugs, security vulnerabilities, and logic flaws in real-world REST APIs without access to their source code.

## 🎯 The Challenge

Participants submit their automated **black-box** testing tools to compete against a benchmark set of **REST APIs**. These APIs contain a variety of intentionally injected issues, ranging from functional defects to common security flaws.

> What is **black-box** testing?
>
> In this context, black-box testing means the tools interact with an API solely via its public endpoints, documented by an **OpenAPI specification**. Tools **generate test cases** by leveraging the specification and the feedback from the API, without looking at the API's internal implementation.

All tools in the competition will be provided with the OpenAPI specification (JSON/YAML) of the REST API to tests, the APIs endpoint, and any required authentication material (e.g., API keys). Tools will not receive the API's source code, database schema, or internal logs.

The *output expected from a tool* is a sequence of HTTP requests/responses (the test cases actually executed against the API) that are used to compute the evaluation metrics.

### 🛠️ Tool Requirements

Tools must meet the following general requirements to participate

* **Automated:** The core testing process must be fully automated and reproducible
* **Black-box:** Must operate strictly without access to the API's source code, interacting with target APIs solely via HTTP requests derived from the provided OpenAPI specification
* **REST-specific:** Must be explicitly designed for REST API testing, general-purpose fuzzers adapted ad-hoc for the competition are discouraged unless genuinely reusable as REST API testing tools
* **Containerized:** Must be easily deployable, via a Docker image
* **Local LLM:** Can only use locally deployed language models (no remote access)

In particular, the tools must be compatible with [RESTgym](https://github.com/SeUniVr/RESTgym), a benchmarking infrastructure specifically designed for REST API testing tools. *Check [here](#-testing-the-testing-tool) the details of the competition experimental setting*. 

### 📊 Evaluation Criteria

Tools will be scored based on a comprehensive set of criteria, focusing on both *quality of testing* and *resource efficiency*.

1. **Fault Detection:** The total number of *unique* `5XX` responses obtained by the tool
2. **Operation Coverage:** The extent of API endpoints successfully tested (obtaining a `2XX` response)
3. **Code Coverage:** The extent of API code effectively explored during testing (measured in terms of methods, statements, and branches covered)
4. **Testing Efficiency:** The time (AUC) taken needed to achieve the fault and coverage results

The final score will be a weighted aggregate of these metrics. 

Uniqueness of `5XX` is in terms of sufficiently distinct error messages, following the criterion used in literature[^1].
Testing metrics will be collected by using the [Restats](https://github.com/SeUniVr/restats) tool.

### 🏆 Awards & Recognition

REST League features a badge-based challenge structure, to highlight tool strengths along distinct dimensions.

- *Fault Detection Challenge*, ranking scores based on the Unique Faults metrics, averaged across all APIs and Z-score normalized
- *Efficiency Challenge*, ranking scores based on the unweighted sum of Z-score-normalized Unique Faults AUC, Operations Covered AUC, and Code Coverage AUC metrics
- *Effectiveness Challenge*, ranking scores based on the unweighted sum of Z-score-normalized Unique Faults, Operations Covered, and Code Coverage metrics

The best performing tool for each challenge will be awarded with a badge.

🥇 **Gold API Tester:** Tool with the highest overall score, winner of the Effectiveness Challenge. <br>
🥈 **Silver API Tester:** Tool with the second-highest overall score, runner-up of the Effectiveness Challenge. <br>
🐞 **Bug Hunter:** Tool with the highest number of unique `5XX` found, winner of the Fault detection Challenge. <br>
⚡ **Roadrunner:** Tool that achieves the highest coverage with the lowest resource consumption footprint, winner of the Efficiency Challenge.

> The tool earning the *Gold API Tester* badge is also the competition's ultimate champion.

Winning tools and their authors will be prominently featured on this GitHub page, recognized at the Awards Ceremony, and invited to present their tool during [ICSE2027](https://conf.researchr.org/home/icse-2027) in Dublin.

### 🎚️ Experimental Setting

Tools will be run by using [RESTgym](https://github.com/SeUniVr/RESTgym), with a time budget of **one hour** for each API. Testing sessions will be repeated **five** times, collecting average results.

All runs will execute in an organizer-controlled sandbox, deployed on proprietary hardware. Network access from within the sandbox is restricted to the target APIs endpoint only. Metrics will be collected by the independent, organizer-run Restats tool included in RESTgym.

Experiments will be executed on a 128-core machine with 386GB of RAM, enabling parallel testing sessions. To each tool, 8 cores and 16GB of RAM will be reserved. The machine used in the experiments is equipped with an Nvidia RTX 4090 video card, available for the tools.

> **LLM Adoption:** To regulate language models usage, remotely accessed LLMs are forbidden. Competing tools can use small or large language models, given they can locally run on the evaluation platform.

#### REST APIs

Tools will be evaluated on a benchmark consisting of **ten** real-world REST APIs. Half of them are APIs already used in testing literature (listed below), and half of them are fresh APIs never used in previous studies (not disclosed to participants).

The benchmark will consist of the following *known* REST APIs (all available in [RESTgym](https://github.com/SeUniVr/RESTgym)):
- Kafka REST Proxy ([GitHub](https://github.com/confluentinc/kafka-rest))
- Flight Search API ([GitHub](https://github.com/Rapter1990/flightsearchapi)) 
- Gestao Hospital ([GitHub](https://github.com/ValchanOficial/GestaoHospital)) 
- Blog API
- Project Tracking System

## 💡 How to Participate

Submit your tool via [EasyChair](https://easychair.org) by 10 November, 2026. We kindly ask interested participants to fill out this [Registration Form](https://forms.gle) before submitting the tool.

1. **Register:** Fill out the *Registration Form* to officially enter your tool
2. **Prepare:** Ensure your tool meets all requirements and is ready for deployment
3. **Submit:** Submit your tool via the *EasyChair* interface, along with detailed setup and execution instructions


### 📚 Publication & Presentation

All authors of tools participating in the competition can submit a *solution paper* describing the tool's approach used to tackle the competition problem. The paper should also discuss the evolution of the tool with respect to previous versions (if any).

Submissions will undergo a *single-blind* peer-review process to assess their technical correctness.
- Papers must be limited to **4 pages** (including references)
- Papers must follow the host conference's formatting guidelines (details [here](https://conf.researchr.org/track/icse-2027/icse-2027-research-track#submission-process))

<br>

> **IEEE Publication:** Accepted solution papers will be included in the ICSE2027 proceedings and published by IEEE.

Authors of accepted solution papers are required to **present their tool** during the competition conference session. The session will be part of the [ICSE2027](https://conf.researchr.org/home/icse-2027) program.

### 🗓️ Competition Timeline

REST League 2027 will be hosted by [ICSE2027](https://conf.researchr.org/home/icse-2027) in Dublin, Ireland, with the following schedule.

| Date (AoE) | Event |
| :--- | :--- |
| **[25/08/2026]** | Call for Participation Opens |
| **[09/10/2026]** | Deadline for Tool Submission |
| **[13/11/2026]** | Notification of Competition Results |
| **[04/12/2026]** | Deadline for Solution Paper Submission |
| **[16/12/2026]** | Solution Papers Response |
| **[06/01/2027]** | Deadline for Solution Paper Revision |
| **[13/01/2027]** | Solution Papers Final Notification |
| **[20/01/2027]** | Deadline for Camera-ready Material |
| **TBA** | **REST League Awards Ceremony** |

## 👑 Competition Results

*TBA*

## 🚀 Boostrapping

To quickly develop your REST API testing tool, you can consider using the [RestTestGen Framework](https://github.com/SeUniVr/RestTestGen). The framework provides many ready-to-use components to:
- parse OpenAPI specifications
- handle HTTP interactions
- model test cases
- generate operation parameter values
- check testing oracles
- mutate HTTP requests
- ... and more

All components and the testing engine are easily customizable, to develop brand new testing tools in minutes. For more details, see the RestTestGen Framework [Wiki](https://seunivr.github.io/RestTestGen-Wiki).

### 🔍 Testing the Testing Tool

Before submitting your tool to REST League, please check its compliance with [RESTgym](https://github.com/SeUniVr/RESTgym) for easy deployment and running on our platform.

You can test your tool on the REST APIs provided in the `apis` directory of this repository (see the specific [apis/README](../apis/README.md) for details) and on the APIs available in RESTgym. 

## 🤝 Organizers & Contact

REST League is organized by

  * **Michele Pasqua**, Univ. of Verona **@** [`michele.pasqua@univr.it`](mailto:michele.pasqua@univr.it)
  * **Mariano Ceccato**, Univ. of Verona **@** [`mariano.ceccato@univr.it`](mailto:mariano.ceccato@univr.it)
  * **Sofia Mari**, Univ. of Verona **@** [`sofia.mari@univr.it`](mailto:sofia.mari@univr.it)
  * **Davide Corradini**, Univ. of Luxembourg **@** [`davide.corradini@uni.lu`](mailto:davide.corradini@uni.lu)

If you have questions, feel free to reach out to us!

<br>

---

[^1]: M. Kim, S. Sinha, and A. Orso. *"Adaptive REST API Testing with Reinforcement Learning"*. In Proceedings of the 38<sup>th</sup> IEEE/ACM International Conference on Automated Software Engineering. ASE2023. IEEE Press, 2024, pp. 446-458.