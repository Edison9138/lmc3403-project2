# Project Testing
This guide talks about different testing methods that will be helpful for this project.

**Contents**
- [Frontend Testing](#frontend-testing) - Testing React state logic and rendering optimization.
- [Backend Testing](#backend-testing) - Logging the output of different LLMs.
- [Database Testing](#database-testing) - Reading content in the database.

## Frontend Testing

Our GUI is written in React using Typescript. This guide is going over a few ways you can test the frontend behavior.

### Independent mode

Run the following in the `root` or `gui` directory.

```sh
npm run gui:indep
```

Internally, there is a custom flag `VITE_GUI_INDEPENDENT` that is set to true when independent mode is ran.
To access this flag in the code, you can use the constant `INDEPENDENT_MODE`, which can be found in `constant.ts`.

```ts
export const INDEPENDENT_MODE: boolean =
  import.meta.env.VITE_GUI_INDEPENDENT === "true" ? true : false;
```

In the independent mode, all api call are dummy calls, allowing you to test frontend behavior without worrying about backend failure. For example, you can change the dummy api call to return error to test how the frontend handles error.

Follow the pattern in `service.ts` to ensure all API calls have a version that works for the independent mode.

### The inspector

On Chrome, right-click --> Inspect to open up the Inspector window. Here are some useful tips that helps with debugging:
- Logic related: `console.log()` allows you to print the result on the "console" tab of the inspector.
- Styling related: <img width="30" alt="selction icon" src="https://github.com/user-attachments/assets/5ee25fa1-f4c8-4f27-be3a-ca1eeffad4a8" /> Click on this icon allows you to hover over elements on the web page and quickly inspect its css properties.

### React Developer Tool

The [react developer tool](https://chromewebstore.google.com/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?pli=1) is a Chrome extension that allows developer to test React optimization on the browser. It you realize certain UI is laggy or re-render multiple times, it might be a good idea to use this tool.

### Remarks
- Why not unit test?
  Jest, or the _JavaScript testing platform_, is a common way to write unit test for JS/TS application. However, we find them to be incomprehensive, offers no flexibility, and painstakingly time-consuming. It is difficult to write unit test, whose goal is to compartmentize each test, when most component needs to get context from its parent or global states. Furthermore, frontend changes constantly, and the result of AI is different everytime, making it not feasible to concretely test frontend behavior with a reasonable amount of time. In short, writing test is just not worth the effort for our seed stage project.

## Backend Testing
Our backend is written in Python with Flask framework. Below are ways to test out some key aspect of the backend code.

### Testing API
You can use Postman or any other API testing tool to access the API endpoint after you have launch the Flask server.

### Testing Backend Logic
You can print out messages in the terminal by writing `print()` in the code. Alternatively, check out `server/utils/Logger.py` to use the Logger class to print out more formatted messages. These print statements are generally enough to test API calls and logic implementation. However, our team has developed more robust logger tools to log the input and output of LLMs. 

### Testing LLM Responses
`server/utils/ChainLogger.py` is an utilty class that shows the input and output of LLM in a formatted pdf. You can find the generated pdf in `server/logs` folder. The pdf comes with information such as latency and messages hidden by the LangChain API that one can't simply access with the print statement.

<img width="372" alt="example pdf output" src="https://github.com/user-attachments/assets/b5e80bd7-2f04-433f-a50e-5eb63683a1a4" />

In order to generate the pdf, you need `pip install pdfkit`, and install wkhtmltopdf and add to PATH on your machine.
- Mac: install with [Homebrew](https://formulae.brew.sh/cask/wkhtmltopdf)
- Windows: follow this [StackOverflow post](https://stackoverflow.com/questions/44661876/python-configure-pdfkit-on-windows)

## Database Testing

We use [Amazon RDS DB](https://aws.amazon.com/rds/?p=ft&c=db&z=3) as Rita’s database and [MySQL Workbench](https://www.mysql.com/products/workbench/) for connection from local host.

**NOTE:** If you need access to the actual database, please consult with the team members. The below section will guide you through setting up a clean environment for testing.

### Setting up Amazon RDS
  - Create an [Amazon Web Services (AWS)](https://aws.amazon.com/) account if you don’t have one yet
  - [Create an Amazon RDS DB instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateDBInstance.html#USER_CreateDBInstance.Creating). Although not required, it is encouraged to use [EC2](https://aws.amazon.com/ec2/?p=pm&c=mt&pd=ec2&z=4) as a bastion server to connect to RDS for better security practice

### Viewing RDS data using MySQL Wrokbench
  - Download and install MySQL Workbench and MySQL Server if you don’t have it yet
    - Windows users can install MySQL using the [MySQL Installer](https://dev.mysql.com/downloads/installer/)
    - Mac users need to download MySQL Workbench and MySQL Server separately. Please refer to [MySQL Server Installer](https://dev.mysql.com/downloads/mysql/) and [MySQL Workbench Installer](https://dev.mysql.com/downloads/workbench/)

Once you have set up RDS and MySQL, create a new connection in MySQL workbench. Click on “Edit Connections” and configure it similarly to the example below. This enables you to use [SSH](https://www.cloudflare.com/learning/access-management/what-is-ssh/) to connect your computer to the EC2 instance connecting the RDS.

<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdIcaBCq8tkTduwWpAVPcYcicF2iAESeXpIQ8wu-mwUXU6pe8Hs8ZYWrppi_ZXbQxCwiZ8Vga1a0--5SsENtHVmMZMlEJxs75jzTC5Wd7gp3wj1_UfccBFtr0et9GZuS1q_Hhpnhw?key=-MOCfIEPYSnC95I2QByPgpqE" width="800" />
**Start Testing**
  - Click on “Test Connection” to make sure the configuration is correct
  - Make sure you have started the EC2 and RDS instances. It usually takes several minutes for RDS to spin up
  - You can write query in MySQL, and the change should be reflected on RDS.

### Remarks
- **Why Amazon RDS?**
  -  Amazon RDS simplifies database management by automating tasks such as provisioning, backups, and patching. This allows you to focus on application development. It also offers scalability to adjust resources based on demand and ensures high availability. In addition, RDS enhances security with features like network isolation and encryption.
- **Why connecting to RDS with EC2?**
  - Connecting to RDS via EC2 allows them to be placed in the same Virtual Private Cloud (VPC), enabling direct and private network connectivity. Additionally, EC2 instances offer flexibility in choosing the appropriate instance type and OS. This allows you to install and configure any required database client software or applications that need to interact with your RDS. 
- **Cost Implications**
  - RDS instances are charged per hour, and additional costs may arise from storage, data transfer, and provisioned IOPS. Comparing these costs to managing a database on an EC2 instance can help determine the most cost-effective solution for your use case.
- **Alternative Connection Methods**
  - If setting up and managing an EC2 bastion host is not preferable, AWS offers alternatives like AWS Systems Manager Session Manager. This service allows secure and auditable connections to your RDS instances without the need for a bastion host. This helps simplifying the architecture and potentially reducing costs. 
