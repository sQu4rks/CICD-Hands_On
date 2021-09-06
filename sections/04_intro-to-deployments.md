# Introduction to Deployments

Software has become far to complex and fast paced to be updated (or *deployed*)
once every year. This is the *Continous Delivery* aspect of CI/CD. Instead of 
having big "push days" where once every year a new version of the software is 
released we do this release process continously thus making smaller incremental
deployments and changes. 

While it is certainly possible to *always* push the newest version of code that 
is being checked into your version control system to production that is not 
advisable. 

A more common way of deploying is to release code to a test deployment where it 
can be tested both manually and automatically(We'll talk about scenario tests 
later in this workshop). 

Over time, this base idea has been altered or adopted to form various *deployment
strategies*. The list below presents these *strategies* without having any claim to 
being complete. 

* **Canary deployments** are deployments where a subset of user requests is routed to the new code thus testing in production with a small user impact. 
* **Shadow deployments** are deployments where both the old and new code run in paralle. User requests
are routed to *both* instances and the new code is tested with actual user requests without the user 
even knowing. 
* **Blue Green deployments** are deployments where two instances (Blue and Green) of the same application run in paralle. All requests are currently served by the Blue instance. The other instance (for this example let's say Green) is updated to the newest version of the code and all requests are now routed to the Green instance. In the case of imminent error the application could be switched back to the Blue instance that runs the previous version of the code. If no errors occure
the cycles repeats itself with Blue being the instance that gets the new code during the next update. 

<div align="right">
   
   [Prev](03_run-project.md) - [Next](05_deploy-to-k8s.md)
</div>