* [CPU Utilization](https://blog.heroix.com/blog/vmware-vcpu-over-allocation)
  * should < 80%
  
* [Ready Time](https://learnvmware.online/2018/03/08/performance-troubleshooting-cpu-ready-time/) - summation in ms
  * graph %RDY should < 5%
  * use esxtop and vROps commands on host to investigate
  * causes:
    * oversubscription - vCPU:pCPU should < 3:1
    * CPU resource limitations on particular VM
    * Resource pool limitations 

* [Readiness](https://communities.vmware.com/thread/545332) - average in percent
  > CPU ready %
  
  > As a shortcut, you can use the following formulas for the default chart update intervals to get the CPU ready %:

  > Realtime: CPU summation value / 200
  
  > Past Day: CPU summation value / 3000
  
  > Past Week: CPU summation value / 18000
  
  > Past Month: CPU summation value / 72000
  
  > Past Year: CPU summation value / 864000

  > Example: A realtime CPU summation value of 1000 is divided by 200 to give a CPU ready % of 5.
  
  > So assuming this VM has 6 vCPU, there is one more step...divide the %Ready value by the number of vCPUs. For your multi-core VM, the formula to convert Ready Summation to a % would be (1612/200)/6=1.34
