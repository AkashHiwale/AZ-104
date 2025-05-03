# Custom Script Extension vs Run Command in Azure VMs

This document covers two approaches to automate post-deployment tasks on Azure Virtual Machines, such as installing software or configuring settings.

## Contents

- [Custom Script Extension](./01_custom_script_extension.md)
- [Run Command](./02_run_command.md)

## ⚖️ When to Use What?

| Feature | Custom Script Extension | Run Command |
|--------|--------------------------|-------------|
| Automation Friendly | ✅ Yes | ⚠️ Limited |
| Interactive Portal Use | ❌ No | ✅ Yes |
| Repeatable Deployments | ✅ Yes | ⚠️ No |
| Debugging & Troubleshooting | ❌ No | ✅ Yes |