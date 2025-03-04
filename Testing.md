# Testing

## Database Connection

- We use [Amazon RDS DB](https://aws.amazon.com/rds/?p=ft&c=db&z=3) as Rita’s database and [MySQL Workbench](https://www.mysql.com/products/workbench/) for connection from local host
- Amazon RDS
  - Create an Amazon Web Services (AWS) account if you don’t have one yet
  - [Create an Amazon RDS DB instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateDBInstance.html#USER_CreateDBInstance.Creating). Although not required, it is encouraged to use [EC2](https://aws.amazon.com/ec2/?p=pm&c=mt&pd=ec2&z=4) as a bastion server to connect to RDS for better security practice
- MySQL Wrokbench
  - Download and install MySQL Workbench and MySQL Server if you don’t have it yet
    - Windows users use [MySQL Installer](https://dev.mysql.com/downloads/installer/)
    - Mac users need to download MySQL Workbench and MySQL Server separately. Please refer to [MySQL Server Installer](https://dev.mysql.com/downloads/mysql/) and [MySQL Workbench Installe](https://dev.mysql.com/downloads/workbench/)r
- Once you have set up RDS and MySQL, create a new connection in MySQL workbench, and click on “Edit Connections” and configure it similarly as below. This enables you to use [SSH](https://www.cloudflare.com/learning/access-management/what-is-ssh/) to connect your computer to the EC2 instance connecting the RDS.
  - ![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdIcaBCq8tkTduwWpAVPcYcicF2iAESeXpIQ8wu-mwUXU6pe8Hs8ZYWrppi_ZXbQxCwiZ8Vga1a0--5SsENtHVmMZMlEJxs75jzTC5Wd7gp3wj1_UfccBFtr0et9GZuS1q_Hhpnhw?key=-MOCfIEPYSnC95I2QByPgpqE)
  - Click on “Test Connection” to make sure the configuration is correct
  - Make sure you have started the EC2 and RDS instances. It usually takes several minutes for RDS to spin up
