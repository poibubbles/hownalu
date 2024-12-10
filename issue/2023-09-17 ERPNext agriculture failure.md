See: https://discuss.frappe.io/t/v14-cant-install-agriculture-app/95340/7

In a nutshell, change the `# Installation` section of `apps/agriculture/agriculture/hooks.py` to:
```
after_install = "agriculture.agriculture.setup.setup_agriculture"
```
..before running `bench install-app agriculture`.