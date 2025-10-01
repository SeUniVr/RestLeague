# REST League

### 🏆 REST API Black-Box Testing Tool Competition

Welcome to **REST League**, the ultimate competition for automated black-box testing tools designed for **RESTful APIs**.

The goal of REST League is to evaluate the performance of open-source and proprietary tools in finding bugs, security vulnerabilities, and logic flaws in real-world REST APIs without access to their source code.

## 🎯 The Challenge

Participants submit their automated **black-box** testing tools to compete against a benchmark set of **REST APIs**. These APIs contain a variety of intentionally injected issues, ranging from functional defects to common security flaws.

> What is **black-box** testing?
>
> In this context, black-box testing means the tools interact with an API solely via its public endpoints, documented by an **OpenAPI specification**. Tools **generate test cases** by leveraging the specification and the feedback from the API, without looking at the API's internal inomplementation.

### 🛠️ Tool Requirements

Tools must meet the following general requirements to participate

* **Automation:** The core testing process must be fully automated and reproducible
* **Black-box:** Must operate strictly without access to the API's source code
* **Target:** Must be explicitly designed to test REST APIs
* **Containerized:** Submissions must be easily deployable, via a Docker image

In particular, the tools must be compatible with [RESTgym](https://github.com/SeUniVr/RESTgym), a benchmarking infrastructure specifically designed for REST API testing tools.

### 📊 Evaluation Criteria

Tools will be scored based on a comprehensive set of criteria, focusing on both **quality of testing** and **resource efficiency**

1. **Fault Detection:** The total number of *unique* `5XX` responses obtained by the tool
2. **Operation Coverage:** The extent of API endpoints succesfully tested (obtaining a `2XX` response)
3. **Code Coverage:** The extend of API code effectively explored during testing (measuread in terms of methods, statements, and branches covered)
4. **Testing Efficiency:** The time taken and the number of requests needed to achieve the fault and coverage results

The final score will be a weighted aggregate of these metrics. Testing metrics will be collected by using the [RESTats](https://github.com/SeUniVr/restats) tool.

## 💡 How to Participate

1. **Register:** Fill out the [**Registration Form**](https://www.google.com) to officially enter your tool
2. **Prepare:** Ensure your tool meets all requirements and is ready for deployment
3. **Submit:** Provide access to your tool, along with detailed setup and execution instructions

> **Sandboxed Execution:** All submitted tools will be run in a secure, isolated, and controlled environment by REST League organizers. Details of the machine running the experiments will be provided upon registration.

### 🗓️ Competition Timeline

REST League will be hosted by [SBFT@ICSE2026](https://search-based-and-fuzz-testing.github.io/sbft26) in Rio de Janeiro, Brazil, with the following schedule.

| Date (AoE) | Event |
| :--- | :--- |
| **[30/10/2025]** | Call for Participation Opens (Tool Submission) |
| **[05/12/2025]** | Final Deadline for Tool Submission |
| **[01/01/2026]** | Notification of results |
| **[26/01/2026]** | Tool report camera ready deadline |
| **TBA** | 🥇 **REST League Awards Ceremony** |

### 🏆 Awards & Recognition

* **🥇 Gold API Tester:** Highest overall score and ultimate champion
* **🥈 Silver API Tester:** Second-highest overall score
* **⭐ Bug Hunter Award:** For the tool with the highest number of unique `5XX` found
* **💻 Efficiency Expert:** For the tool that achieves high coverage with the lowest resource consumption footprint

Winning tools and their creators will be prominently featured on this GitHub page, recognized at the Awards Ceremony, and invited to present their tool during [SBFT@ICSE2026](https://search-based-and-fuzz-testing.github.io/sbft26) in Rio.

## 🤝 Organizers & Contact

REST League is organized by

  * **Michele Pasqua**, Univ. of Verona **@** [`michele.pasqua@univr.it`](mailto:michele.pasqua@univr.it)
  * **Mariano Ceccato**, Univ. of Verona **@** [`mariano.ceccato@univr.it`](mailto:mariano.ceccato@univr.it)
  * **Sofia Mari**, Univ. of Verona **@** [`sofia.mari@univr.it`](mailto:sofia.mari@univr.it)
  * **Davide Corradini**, Univ. of Luxembourg **@** [`davide.corradini@uni.lu`](mailto:davide.corradini@uni.lu)

If you have questions, feel free to reach out to us!

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

You can test your tool on the REST APIs provided in the `apis` directory of this repository (see the specific [README](apis/README.md) for details). An example testing tool is provided in the `tools` directory of this repository (see the specific [README](tools/README.md) for details).

> **TODO:** section to be expanded