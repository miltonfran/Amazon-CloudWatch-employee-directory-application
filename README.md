<h1>Amazon-CloudWatch-employee-directory-application</h1>

<h2>Description</h2>
We've already deployed resources into our AWS account with the employee directory application, so to get a handle on what CloudWatch is and how it works.
The end goal is to set up a dashboard that shows us the CPU utilization of the EC2 instance over time and set an alert that will be sent out if the CPU utilization of the instance goes over 60% for a period of time.
<br />

<h2>Program walk-through:</h2>

1. Navigate to Amazon CloudWatch (Many AWS services begin reporting metrics to CloudWatch automatically when you create resources).
- Let's first create a dashboard (A dashboard in CloudWatch is a customizable page in the console that you can use to monitor your different types of resources in a single view, including resources spread
across different AWS regions).
- click dashboards in the left-hand navigation and then click create a dashboard and we can then name this dashboard mydashboard.
- AWS resources automatically send metrics to CloudWatch and it's built into the service, I'm going to select which widget we can add to the dashboard, and I will select a line graph here.
- Next, we can take a look at what the data source will be for this widget, and I will select metric for this.
- We can browse through all of the available metrics, this is organized by service, so I will find EC2, I will select EC2, and then I want to view per instance metrics.
- Scroll through the different EC2-specific metrics that are being reported to CloudWatch and I want to select CPU utilization
- Click save, and now we are brought back to the dashboard with one line graph for one specific instance's CPU utilization (This gives us visibility into one aspect of the health of our EC2 instance).
- with EC2 and CloudWatch, you only get visibility into the health of the instance by default, which doesn't really give you a holistic picture of the health of your application.
The application running on the instance might not be operating correctly, but the CPU utilization could be fine, so keep in mind that you may choose to use custom metricsto get a more detailed and accurate view of the health in these dashboards, Once a dashboard is created, you can then share it with your team members.
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742577926/Screenshot_2025-03-20_185314_gwqflx.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742577995/Screenshot_2025-03-20_185340_krn46d.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742578049/Screenshot_2025-03-20_185418_oktrnw.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742583007/Screenshot_2025-03-20_185500_tphknn.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742583015/Screenshot_2025-03-20_185532_zyhpqi.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742583024/Screenshot_2025-03-20_185546_h85zcx.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742583029/Screenshot_2025-03-20_185646_xsfrm4.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742583042/Screenshot_2025-03-20_185704_uxzdkr.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742583057/Screenshot_2025-03-20_190032_arq2mu.png"/>
<br />


2. CloudWatch alarms allow you to create thresholds for the metrics you're monitoring, and these thresholds can define normal boundaries for the values of the metrics, If a metric crosses a boundary for a period of time, the alarm would be triggered, and then you can take a couple of different automated actions after an alarm is triggered.
-  I want to notify someone if the CPU utilization spikes over 70% for a period of time, say five minutes
-  Let's create an alarm to do that, navigate to the Alarm section and click Create alarm
-  Create an alarm for CPU utilization, so I will select metric, click on EC2, per instance metrics and scroll down to select CPU utilization.
-  select the time period we are monitoring to trigger the alarm, which in this case is five minutes, (want to make sure you pick a reasonable time period where you don't wait too long to respond but you also don't respond to every short-lived uptick in CPU utilization).
-  There is a balance to strike here and it will be highly dependent on your specific situation and your desired outcome
-  scroll down and type in 70 for the static threshold, which we are watching for, which is representing the CPU utilization threshold (If it goes over 70% for more than five minutes, it's likely that there's a problem, and now we will configure the action that will be taken if the metric triggers the alarm).
-  Next, we will configure the action that will be taken if the metric triggers the alarm (For CloudWatch alarms, there are three states an alarm can be in: either an ALARM, OK, or INSUFFICIENT_DATA. An alarm can trigger an action when it transitions between these three states).
-  send out an alert to an email address when it transitions from OK to an alarm.
-  (AWS has a service called Amazon Simple Notification Service, or SNS, which allows you to create a topic and then send out messages to subscribers of the topic, You can imagine a scenario where we have systems admins or developers on call for our employee directory application and if something goes wrong, we want to send them an email paging them, letting them know that something is going wrong with the app).
-  Select create a new SNS topic since we do not have one in place already. Name it CPU_Utilization_Topic, and then I will put in an email address here to receive the alert.

<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592026/Screenshot_2025-03-20_190126_ztrcrt.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592029/Screenshot_2025-03-20_190358_xts2jr.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592038/Screenshot_2025-03-20_190716_m8mgco.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592044/Screenshot_2025-03-20_190854_rfh2mh.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592054/Screenshot_2025-03-20_190918_ffm584.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592060/Screenshot_2025-03-20_190954_qzolra.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592066/Screenshot_2025-03-20_191139_heb5gm.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592072/Screenshot_2025-03-20_191237_kdaw6r.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1742592078/Screenshot_2025-03-20_191254_vg8kyc.png"/>
<br />























