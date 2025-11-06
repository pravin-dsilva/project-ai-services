# Troubleshooting

This section helps diagnose and resolve common issues encountered while using the tool.

Before reporting any issue, we recommend re-configuring the environment and validating the setup.

```bash
~ % ai-services bootstrap configure
Running bootstrap configuration...
✅ Current user is root.
✅ Podman already configured
✅ IBM Spyre Accelerator is attached to the LPAR
ServiceReport output: servicereport 2.2.5

Spyre configuration checks             PASS

 VFIO Driver configuration             PASS
 User memlock configuration            PASS
 sos config                    PASS   Auto Fixed
 sos package                    PASS
 VFIO udev rules configuration           PASS
 User group configuration             PASS   Auto Fixed
 VFIO device permission              PASS
 VFIO kernel module loaded             PASS
 VFIO module dep configuration           PASS

Memlock limit is set for the sentient group.
Spyre user must be in the sentient group.
To add run below command:
	sudo usermod -aG sentient <user>
	Example:
	sudo usermod -aG sentient abc
	Re-login as <user>.

✅ Spyre cards configuration validated successfully.
✅ Bootstrap configuration completed successfully.


~ % ai-services bootstrap validate
Running bootstrap validation...
✅ Current user is root.
✅ Operating system is RHEL	{"version": "9.6"}
✅ System is registered with RHN
✅ System is running on IBM Power11 architecture
✅ IBM Spyre Accelerator is attached to the LPAR
✅ All validations passed
```

## Common Issues

### 1. Pod already exists

#### Symptom: 

```bash
Error: layer 1: failed pod creation: failed to execute podman kube play: playing YAML file: adding pod to state: name "test--vllm-server" is in use: pod already exists
```

#### Possible Causes:

- Application creation failed during execution.
- Application creation stopped unexpectedly before completion.
- Application teardown failed or was skipped.
- Application name is redundant.

#### Resolution:

1. Check if any partial resources are still active.

    ```bash
    ai-services application ps
    ```

2. If the conflicting pod shows up, manually clean up the pod and any residue from the application left behind.

    ```bash
    ai-services application delete <application_name>
    ```

### 2. Image pull denied

#### Symptom: 

```bash
Error: layer 1: failed pod creation: f...image configuration: fetching blob: denied: Your account has exceeded its pull traffic quota for the current month.
```

#### Resolution:

Contact project-ai-service if you hit this error. (Placeholder)
