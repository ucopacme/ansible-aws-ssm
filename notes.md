# Activation

```
aws ssm create-activation --default-instance-name "MyServers" --iam-role "MyAutomationRole" --registration-limit 100
```

# Inventory

```
aws ssm get-inventory | jq '.Entities[].Data["AWS:InstanceInformation"]'
```

sorted list of computer names

```
aws ssm get-inventory | jq -r '.Entities[].Data["AWS:InstanceInformation"].Content[].ComputerName' |sort
```
