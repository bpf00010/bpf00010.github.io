# Experience

## Higher-education IT

I work with the systems behind Windows and Linux computer labs: preparing images, starting deployments, managing configuration, and making domain logins less painful.

### Lab deployments

I use SCCM/MECM device collections and task sequences to queue Windows lab deployments. The time until the lab machines begin running the task sequence together went from around an hour to about 3–5 minutes. Proxmox VE hosts our golden image VMs and licensing servers, and I also work with GitLab-hosted Ubuntu autoinstall ISOs.

[How the deployment workflow fits together](engineering/lab-provisioning.md)

### Linux management

My GitLab-to-AWX pipeline syncs playbook changes and rebuilds the Execution Environment automatically. I keep job launches manual so I can control when changes reach the machines. AWX connects to machines over SSH to apply configuration and compliance policies, including Linux LAPS password rotation, with custom Execution Environments providing the job runtime.

[Inside the AWX workflow](engineering/awx-orchestration.md)

### Directory performance

I edited `sssd.conf` to limit nested-group and forest lookups, disable dynamic DNS updates, narrow group permission searches, use permissive GPO evaluation, and cache directory information for four hours. Together, those changes reduced domain login times from about 60 to 10 seconds across 100 Ubuntu workstations.

[What changed in SSSD](engineering/sssd-tuning.md)

### HPC and server-room work

I helped set up eight high-performance computing (HPC) nodes in a server room, handling OS installation and cluster configuration.

I also centrally managed user profiles and environment setups for specific AI/ML learning needs, including Docker and Anaconda setups. That work covered both getting the nodes running and preparing the environments people needed to use them.

## Education

I'm studying Management Information Systems at West Virginia University.
