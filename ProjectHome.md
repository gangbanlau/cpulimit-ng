Based on sourceforge cpulimit project. Many bug fixed.

below information is from cpulimit@sf

What is it?
cpulimit is a simple program which attempts to limit the cpu usage of a process (expressed in percentage, not in cpu time). This is useful to control batch jobs, when you don't want them to eat too much cpu. It does not act on the nice value or other scheduling priority stuff, but on the real cpu usage. Also, it is able to adapt itself to the overall system load, dynamically and quickly.

System Requirements
cpulimit should run on every Linux 2.2 or greater. It has been reported by several users that cpulimit works fine even on SMP hardware, but consider that if you have more than one cpu there is a little difference in the meaning of cpu usage (see below).
If you can modify the source code of cpulimit to make it run in another OS, please notify me, so I can publish your code. I think that the only non-portable code is to iterate through the process list and get process statistics.

Examples of use
Limit the process 'bigloop' by executable name to 40% CPU:

> cpulimit --exe bigloop --limit 40
> cpulimit --exe /usr/local/bin/bigloop --limit 40

Limit a process by PID to 55% CPU:

> cpulimit --pid 2960 --limit 55

Launch a process by command line and limit it to 40% (in development version only!):

> cpulimit --limit 40 /etc/rc.d/rc.boinc start

Notes

If your machine has one processor you can limit the percentage from 0% to 100%, which means that if you set for example 50%, your process cannot use more than 500 ms of cpu time for each second. But if your machine has four processors, percentage may vary from 0% to 400%, so setting the limit to 200% means to use no more than half of the available power. In any case, the percentage is the same of what you see when you run top.
