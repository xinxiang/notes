* [Ready Time](https://learnvmware.online/2018/03/08/performance-troubleshooting-cpu-ready-time/)
  * graph %RDY should < 5%
  * use esxtop and vROps commands on host to investigate
  * causes:
    * oversubscription - vCPU:pCPU should < 3:1
    * CPU resource limitations on particular VM
    * Resource pool limitations 
