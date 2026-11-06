
- **Student name:** Peng Seyha
- **Student ID:** e20220620
- **Learner Lab user name:** 
- **Date completed:**

---

## Security groups

![LoadBalancerSecurityGroup](images/01-sg-load-balancer.png)

![LaunchTemplateSecurityGroup](images/02-sg-launch-template.png)

## Target group

![LoadBalancerTargetGroup](images/03-target-group.png)

![Health checks](images/04-health-checks.png)

## Application Load Balancer

![Load balancer list](images/05-load-balancer-list.png)

![Load balancer details](images/06-load-balancer-details.png)

## Launch template

![AutoScalingLaunchTemplate](images/07-launch-template.png)

## Auto Scaling group

![Auto Scaling groups](images/08-asg-list.png)

![Auto Scaling group details](images/09-asg-details.png)

## Load balancing test

![First request](images/10-browser-1.png)

![Second request, different host](images/11-browser-2.png)

## Simulated application failure

![Stopping httpd](images/12-stop-httpd.png)

![Target unhealthy or draining](images/13-target-unhealthy.png)

![New target healthy](images/14-target-replaced.png)

## Questions

1. Why does the page show a different hostname when you refresh it?
2. After you stopped `httpd`, the instance was still *running* in EC2, but the target group marked it *unhealthy*. What did the health check test, and why did the instance fail it?
3. Who replaced the failed instance: the load balancer, the target group, or the Auto Scaling group? Explain the role of each one.
4. With desired 2, minimum 2 and maximum 3, how many instances run normally? In what situation could there be 3?
5. The instances' security group allows HTTP from anywhere. How could you change it so that the instances accept HTTP **only** from the load balancer?

### Answers
1. The page shows a different hostname because the load balancer sends requests to different EC2 instances. When I refresh the page, it may connect to another instance.

2. The health check tested whether the web server was responding to HTTP requests. After I stopped httpd, the instance was still running, but the web server was not responding, so it was marked as unhealthy.

3. The Auto Scaling group replaced the failed instance. The load balancer distributes traffic, the target group checks instance health, and the Auto Scaling group maintains the required number of instances.

4. Normally, 2 instances are running because the desired capacity is 2. It can increase to 3 when more capacity is needed and a scaling policy is configured.

5. I can remove the HTTP rule that allows traffic from anywhere (0.0.0.0/0) and add a new rule on port 80 that only allows traffic from the load balancer's security group.

---

