# Starting a whole lab deployment in minutes

**Environment:** Higher-education IT · Windows and Ubuntu labs

When you're deploying an entire lab, even getting the job started can take too much time. My work brings image preparation and device collections together so the lab machines begin running their Windows deployment task sequence together in about **3–5 minutes**, down from roughly **an hour**.

That timing runs through the machines starting the task sequence together. Completing the OS deployment takes additional time.

## Where Proxmox fits

Proxmox VE is where we host golden images or capture them from. It also hosts licensing servers. In this workflow, its role is to provide the virtual machines behind those images and services.

## Windows: capture, collections, and task sequences

Windows images are captured and deployed through SCCM/MECM. Device collections let us target large groups of lab machines together, then queue the appropriate task sequence for that collection.

The practical difference is how much work it takes to kick off a lab deployment. Instead of spending around an hour getting it started, the machines begin running the task sequence together within about 3–5 minutes.


## Ubuntu: repeatable installation media

For Ubuntu, I work with GitLab-hosted autoinstall ISOs. These carry the installation choices into the deployment process, reducing the setup that needs to be repeated by hand.

## After installation

Getting an OS installed is one part of managing a lab. On the Linux side, [AWX applies ongoing configuration and compliance policies over SSH](awx-orchestration.md), including Linux LAPS password rotation.
