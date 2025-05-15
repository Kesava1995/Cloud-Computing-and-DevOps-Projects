Microsoft Windows [Version 10.0.26100.3915]
(c) Microsoft Corporation. All rights reserved.

C:\Users\nvpke>az login
Select the account you want to log in with. For more information on login with Azure CLI, see https://go.microsoft.com/fwlink/?linkid=2271136

Retrieving tenants and subscriptions for the selection...

[Tenant and subscription selection]

No     Subscription name       Subscription ID                       Tenant
-----  ----------------------  ------------------------------------  ----------------------
[1] *  Simplilearn HOL 100744  b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8  Simplilearn HOL 100744

The default is marked with an *; the default tenant is 'Simplilearn HOL 100744' and subscription is 'Simplilearn HOL 100744' (b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8).

Select a subscription and tenant (Type a number or Enter for no changes):

Tenant: Simplilearn HOL 100744
Subscription: Simplilearn HOL 100744 (b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8)

[Announcements]
With the new Azure CLI login experience, you can select the subscription you want to use more easily. Learn more about it and its configuration at https://go.microsoft.com/fwlink/?linkid=2271236

If you encounter any problem, please open an issue at https://aka.ms/azclibug

[Warning] The login output has been updated. Please be aware that it no longer displays the full list of available subscriptions by default.


C:\Users\nvpke>D:

D:\>cd 0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az group create --name RandRG --location eastus
{
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG",
  "location": "eastus",
  "managedBy": null,
  "name": "RandRG",
  "properties": {
    "provisioningState": "Succeeded"
  },
  "tags": null,
  "type": "Microsoft.Resources/resourceGroups"
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network vnet create --resource-group RandRG --name RandVNet --address-prefix 10.0.0.0/16 --subnet-name WebSubnet --subnet-prefix 10.0.1.0/24
{
  "newVNet": {
    "addressSpace": {
      "addressPrefixes": [
        "10.0.0.0/16"
      ]
    },
    "enableDdosProtection": false,
    "etag": "W/\"952addf1-7f8c-4147-b627-fd9c707ad8a0\"",
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/virtualNetworks/RandVNet",
    "location": "eastus",
    "name": "RandVNet",
    "privateEndpointVNetPolicies": "Disabled",
    "provisioningState": "Succeeded",
    "resourceGroup": "RandRG",
    "resourceGuid": "c0d21f10-6bfa-4588-aa7b-47470f126ca1",
    "subnets": [
      {
        "addressPrefix": "10.0.1.0/24",
        "delegations": [],
        "etag": "W/\"952addf1-7f8c-4147-b627-fd9c707ad8a0\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/virtualNetworks/RandVNet/subnets/WebSubnet",
        "name": "WebSubnet",
        "privateEndpointNetworkPolicies": "Disabled",
        "privateLinkServiceNetworkPolicies": "Enabled",
        "provisioningState": "Succeeded",
        "resourceGroup": "RandRG",
        "type": "Microsoft.Network/virtualNetworks/subnets"
      }
    ],
    "type": "Microsoft.Network/virtualNetworks",
    "virtualNetworkPeerings": []
  }
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network public-ip create --resource-group RandRG --name RandPublicIP --sku Standard --allocation-method static
[Coming breaking change] In the coming release, the default behavior will be changed as follows when sku is Standard and zone is not provided: For zonal regions, you will get a zone-redundant IP indicated by zones:["1","2","3"]; For non-zonal regions, you will get a non zone-redundant IP indicated by zones:null.
{
  "publicIp": {
    "ddosSettings": {
      "protectionMode": "VirtualNetworkInherited"
    },
    "etag": "W/\"2f2c0d86-8673-470b-bc5a-14511dfd84b5\"",
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/publicIPAddresses/RandPublicIP",
    "idleTimeoutInMinutes": 4,
    "ipAddress": "52.191.117.191",
    "ipTags": [],
    "location": "eastus",
    "name": "RandPublicIP",
    "provisioningState": "Succeeded",
    "publicIPAddressVersion": "IPv4",
    "publicIPAllocationMethod": "Static",
    "resourceGroup": "RandRG",
    "resourceGuid": "10632848-85e3-4fdf-b4cd-2567db5b5e1b",
    "sku": {
      "name": "Standard",
      "tier": "Regional"
    },
    "type": "Microsoft.Network/publicIPAddresses"
  }
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network lb create --resource-group RandRG --name RandLB --sku Standard --location eastus --frontend-ip-name RandFrontEnd --backend-pool-name RandBackEndPool --public-ip-address RandPublicIP
{
  "loadBalancer": {
    "backendAddressPools": [
      {
        "etag": "W/\"e8530784-7d17-4bdd-95f0-d286029c5eba\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/backendAddressPools/RandBackEndPool",
        "name": "RandBackEndPool",
        "properties": {
          "loadBalancerBackendAddresses": [],
          "provisioningState": "Succeeded"
        },
        "resourceGroup": "RandRG",
        "type": "Microsoft.Network/loadBalancers/backendAddressPools"
      }
    ],
    "frontendIPConfigurations": [
      {
        "etag": "W/\"e8530784-7d17-4bdd-95f0-d286029c5eba\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/frontendIPConfigurations/RandFrontEnd",
        "name": "RandFrontEnd",
        "properties": {
          "privateIPAllocationMethod": "Dynamic",
          "provisioningState": "Succeeded",
          "publicIPAddress": {
            "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/publicIPAddresses/RandPublicIP",
            "resourceGroup": "RandRG"
          }
        },
        "resourceGroup": "RandRG",
        "type": "Microsoft.Network/loadBalancers/frontendIPConfigurations"
      }
    ],
    "inboundNatPools": [],
    "inboundNatRules": [],
    "loadBalancingRules": [],
    "outboundRules": [],
    "probes": [],
    "provisioningState": "Succeeded",
    "resourceGuid": "5a8e8371-5f78-48c4-8861-5b916d29051f"
  }
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network lb probe create --resource-group RandRG --lb-name RandLB --name RandHealthProbe --protocol tcp --port 80 --interval 15 --threshold 4
The property "numberOfProbes" is not respected. Load Balancer health probes will probe up or down immediately after one probe regardless of the property's configured value. To control the number of successful or failed consecutive probes necessary to mark backend instances as healthy or unhealthy, please leverage the property "probeThreshold" instead.
{
  "etag": "W/\"34e5578b-8fd4-4187-b86b-911fdd3367c5\"",
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/probes/RandHealthProbe",
  "intervalInSeconds": 15,
  "name": "RandHealthProbe",
  "numberOfProbes": 4,
  "port": 80,
  "probeThreshold": 1,
  "protocol": "Tcp",
  "provisioningState": "Succeeded",
  "resourceGroup": "RandRG",
  "type": "Microsoft.Network/loadBalancers/probes"
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network lb rule create --resource-group RandRG --lb-name RandLB --name RandHTTPRule --protocol tcp --frontend-port 80 --backend-port 80 --frontend-ip-name RandFrontEnd --backend-pool-name RandBackEndPool --probe-name RandHealthProbe
{
  "backendAddressPool": {
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/backendAddressPools/RandBackEndPool",
    "resourceGroup": "RandRG"
  },
  "backendAddressPools": [
    {
      "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/backendAddressPools/RandBackEndPool",
      "resourceGroup": "RandRG"
    }
  ],
  "backendPort": 80,
  "disableOutboundSnat": false,
  "enableFloatingIP": false,
  "enableTcpReset": false,
  "etag": "W/\"3149ded0-4177-41a9-93fb-4c66daaa4afe\"",
  "frontendIPConfiguration": {
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/frontendIPConfigurations/RandFrontEnd",
    "resourceGroup": "RandRG"
  },
  "frontendPort": 80,
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/loadBalancingRules/RandHTTPRule",
  "idleTimeoutInMinutes": 4,
  "loadDistribution": "Default",
  "name": "RandHTTPRule",
  "probe": {
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/probes/RandHealthProbe",
    "resourceGroup": "RandRG"
  },
  "protocol": "Tcp",
  "provisioningState": "Succeeded",
  "resourceGroup": "RandRG",
  "type": "Microsoft.Network/loadBalancers/loadBalancingRules"
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network nsg create --resource-group RandRG --name RandNSG --location eastus
{
  "NewNSG": {
    "defaultSecurityRules": [
      {
        "access": "Allow",
        "description": "Allow inbound traffic from all VMs in VNET",
        "destinationAddressPrefix": "VirtualNetwork",
        "destinationAddressPrefixes": [],
        "destinationPortRange": "*",
        "destinationPortRanges": [],
        "direction": "Inbound",
        "etag": "W/\"93ea7de1-2324-411d-8d0c-50a8d5fc0ddd\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG/defaultSecurityRules/AllowVnetInBound",
        "name": "AllowVnetInBound",
        "priority": 65000,
        "protocol": "*",
        "provisioningState": "Succeeded",
        "resourceGroup": "RandRG",
        "sourceAddressPrefix": "VirtualNetwork",
        "sourceAddressPrefixes": [],
        "sourcePortRange": "*",
        "sourcePortRanges": [],
        "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
      },
      {
        "access": "Allow",
        "description": "Allow inbound traffic from azure load balancer",
        "destinationAddressPrefix": "*",
        "destinationAddressPrefixes": [],
        "destinationPortRange": "*",
        "destinationPortRanges": [],
        "direction": "Inbound",
        "etag": "W/\"93ea7de1-2324-411d-8d0c-50a8d5fc0ddd\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG/defaultSecurityRules/AllowAzureLoadBalancerInBound",
        "name": "AllowAzureLoadBalancerInBound",
        "priority": 65001,
        "protocol": "*",
        "provisioningState": "Succeeded",
        "resourceGroup": "RandRG",
        "sourceAddressPrefix": "AzureLoadBalancer",
        "sourceAddressPrefixes": [],
        "sourcePortRange": "*",
        "sourcePortRanges": [],
        "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
      },
      {
        "access": "Deny",
        "description": "Deny all inbound traffic",
        "destinationAddressPrefix": "*",
        "destinationAddressPrefixes": [],
        "destinationPortRange": "*",
        "destinationPortRanges": [],
        "direction": "Inbound",
        "etag": "W/\"93ea7de1-2324-411d-8d0c-50a8d5fc0ddd\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG/defaultSecurityRules/DenyAllInBound",
        "name": "DenyAllInBound",
        "priority": 65500,
        "protocol": "*",
        "provisioningState": "Succeeded",
        "resourceGroup": "RandRG",
        "sourceAddressPrefix": "*",
        "sourceAddressPrefixes": [],
        "sourcePortRange": "*",
        "sourcePortRanges": [],
        "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
      },
      {
        "access": "Allow",
        "description": "Allow outbound traffic from all VMs to all VMs in VNET",
        "destinationAddressPrefix": "VirtualNetwork",
        "destinationAddressPrefixes": [],
        "destinationPortRange": "*",
        "destinationPortRanges": [],
        "direction": "Outbound",
        "etag": "W/\"93ea7de1-2324-411d-8d0c-50a8d5fc0ddd\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG/defaultSecurityRules/AllowVnetOutBound",
        "name": "AllowVnetOutBound",
        "priority": 65000,
        "protocol": "*",
        "provisioningState": "Succeeded",
        "resourceGroup": "RandRG",
        "sourceAddressPrefix": "VirtualNetwork",
        "sourceAddressPrefixes": [],
        "sourcePortRange": "*",
        "sourcePortRanges": [],
        "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
      },
      {
        "access": "Allow",
        "description": "Allow outbound traffic from all VMs to Internet",
        "destinationAddressPrefix": "Internet",
        "destinationAddressPrefixes": [],
        "destinationPortRange": "*",
        "destinationPortRanges": [],
        "direction": "Outbound",
        "etag": "W/\"93ea7de1-2324-411d-8d0c-50a8d5fc0ddd\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG/defaultSecurityRules/AllowInternetOutBound",
        "name": "AllowInternetOutBound",
        "priority": 65001,
        "protocol": "*",
        "provisioningState": "Succeeded",
        "resourceGroup": "RandRG",
        "sourceAddressPrefix": "*",
        "sourceAddressPrefixes": [],
        "sourcePortRange": "*",
        "sourcePortRanges": [],
        "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
      },
      {
        "access": "Deny",
        "description": "Deny all outbound traffic",
        "destinationAddressPrefix": "*",
        "destinationAddressPrefixes": [],
        "destinationPortRange": "*",
        "destinationPortRanges": [],
        "direction": "Outbound",
        "etag": "W/\"93ea7de1-2324-411d-8d0c-50a8d5fc0ddd\"",
        "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG/defaultSecurityRules/DenyAllOutBound",
        "name": "DenyAllOutBound",
        "priority": 65500,
        "protocol": "*",
        "provisioningState": "Succeeded",
        "resourceGroup": "RandRG",
        "sourceAddressPrefix": "*",
        "sourceAddressPrefixes": [],
        "sourcePortRange": "*",
        "sourcePortRanges": [],
        "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
      }
    ],
    "etag": "W/\"93ea7de1-2324-411d-8d0c-50a8d5fc0ddd\"",
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG",
    "location": "eastus",
    "name": "RandNSG",
    "provisioningState": "Succeeded",
    "resourceGroup": "RandRG",
    "resourceGuid": "5711287a-a8a7-49f2-b919-4c9334f90514",
    "securityRules": [],
    "type": "Microsoft.Network/networkSecurityGroups"
  }
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network nsg rule create --resource-group RandRG --nsg-name RandNSG --name AllowHTTP --protocol Tcp --direction Inbound --priority 1000 --source-address-prefixes '*' --source-port-ranges '*' --destination-address-prefixes '*' --destination-port-ranges 80 --access Allow
{
  "access": "Allow",
  "destinationAddressPrefix": "*",
  "destinationAddressPrefixes": [],
  "destinationPortRange": "80",
  "destinationPortRanges": [],
  "direction": "Inbound",
  "etag": "W/\"f5c0e2ca-c68e-4127-8531-a6fecfebe559\"",
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG/securityRules/AllowHTTP",
  "name": "AllowHTTP",
  "priority": 1000,
  "protocol": "Tcp",
  "provisioningState": "Succeeded",
  "resourceGroup": "RandRG",
  "sourceAddressPrefix": "*",
  "sourceAddressPrefixes": [],
  "sourcePortRange": "*",
  "sourcePortRanges": [],
  "type": "Microsoft.Network/networkSecurityGroups/securityRules"
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network vnet subnet update --vnet-name RandVNet --name WebSubnet --resource-group RandRG --network-security-group RandNSG
{
  "addressPrefix": "10.0.1.0/24",
  "delegations": [],
  "etag": "W/\"99e94d1f-7f50-4ba7-96f0-1d0ca48c6804\"",
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/virtualNetworks/RandVNet/subnets/WebSubnet",
  "name": "WebSubnet",
  "networkSecurityGroup": {
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkSecurityGroups/RandNSG",
    "resourceGroup": "RandRG"
  },
  "privateEndpointNetworkPolicies": "Disabled",
  "privateLinkServiceNetworkPolicies": "Enabled",
  "provisioningState": "Succeeded",
  "resourceGroup": "RandRG",
  "type": "Microsoft.Network/virtualNetworks/subnets"
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az vm create --resource-group RandRG --name RandVM1 --image Win2019Datacenter --vnet-name RandVNet --subnet WebSubnet --admin-username azureuser --admin-password Pa$$w0rd1234! --nsg "" --size Standard_B2s --public-ip-address "" --storage-sku Standard_LRS
{
  "fqdns": "",
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Compute/virtualMachines/RandVM1",
  "location": "eastus",
  "macAddress": "00-0D-3A-9B-87-DC",
  "powerState": "VM running",
  "privateIpAddress": "10.0.1.4",
  "publicIpAddress": "",
  "resourceGroup": "RandRG",
  "zones": ""
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az vm create --resource-group RandRG --name RandVM2 --image Win2019Datacenter --vnet-name RandVNet --subnet WebSubnet --admin-username azureuser --admin-password Pa$$w0rd1234! --nsg "" --size Standard_B2s --public-ip-address "" --storage-sku Standard_LRS
{
  "fqdns": "",
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Compute/virtualMachines/RandVM2",
  "location": "eastus",
  "macAddress": "60-45-BD-EF-8F-86",
  "powerState": "VM running",
  "privateIpAddress": "10.0.1.5",
  "publicIpAddress": "",
  "resourceGroup": "RandRG",
  "zones": ""
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>FOR /F "delims=" %%i IN ('az network nic show --name RandVM1VMNic --resource-group RandRG --query "ipConfigurations[0].name" -o tsv') DO SET IP1=%%i
%%i was unexpected at this time.

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>FOR /F "delims=" %i IN ('az network nic show --name RandVM1VMNic --resource-group RandRG --query "ipConfigurations[0].name" -o tsv') DO SET IP1=%i

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>SET IP1=ipconfigRandVM1

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network nic show --name RandVM1VMNic --resource-group RandRG --query "ipConfigurations[0].name" -o tsv
ipconfigRandVM1

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>FOR /F "delims=" %i IN ('az network nic show --name RandVM1VMNic --resource-group RandRG --query "ipConfigurations[0].name" -o tsv') DO SET IP1=%i

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>SET IP1=ipconfigRandVM1

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>echo %IP1%
ipconfigRandVM1

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>FOR /F "delims=" %i IN ('az network nic show --name RandVM2VMNic --resource-group RandRG --query "ipConfigurations[0].name" -o tsv') DO SET IP2=%i

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>SET IP2=ipconfigRandVM2

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network nic ip-config address-pool add --address-pool RandBackEndPool --ip-config-name %IP1% --nic-name RandVM1VMNic --resource-group RandRG --lb-name RandLB
{
  "etag": "W/\"adc91803-ac16-4dad-8b36-2f0a22d5cf31\"",
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkInterfaces/RandVM1VMNic/ipConfigurations/ipconfigRandVM1",
  "loadBalancerBackendAddressPools": [
    {
      "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/backendAddressPools/RandBackEndPool",
      "resourceGroup": "RandRG"
    }
  ],
  "name": "ipconfigRandVM1",
  "primary": true,
  "privateIPAddress": "10.0.1.4",
  "privateIPAddressVersion": "IPv4",
  "privateIPAllocationMethod": "Dynamic",
  "provisioningState": "Succeeded",
  "resourceGroup": "RandRG",
  "subnet": {
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/virtualNetworks/RandVNet/subnets/WebSubnet",
    "resourceGroup": "RandRG"
  },
  "type": "Microsoft.Network/networkInterfaces/ipConfigurations"
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network nic ip-config address-pool add --address-pool RandBackEndPool --ip-config-name %IP2% --nic-name RandVM2VMNic --resource-group RandRG --lb-name RandLB
{
  "etag": "W/\"8187c80f-51f5-4fb0-b20b-b588feea08b5\"",
  "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/networkInterfaces/RandVM2VMNic/ipConfigurations/ipconfigRandVM2",
  "loadBalancerBackendAddressPools": [
    {
      "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/loadBalancers/RandLB/backendAddressPools/RandBackEndPool",
      "resourceGroup": "RandRG"
    }
  ],
  "name": "ipconfigRandVM2",
  "primary": true,
  "privateIPAddress": "10.0.1.5",
  "privateIPAddressVersion": "IPv4",
  "privateIPAllocationMethod": "Dynamic",
  "provisioningState": "Succeeded",
  "resourceGroup": "RandRG",
  "subnet": {
    "id": "/subscriptions/b51988b6-5bdb-4295-bbd3-6d01b1bf3ed8/resourceGroups/RandRG/providers/Microsoft.Network/virtualNetworks/RandVNet/subnets/WebSubnet",
    "resourceGroup": "RandRG"
  },
  "type": "Microsoft.Network/networkInterfaces/ipConfigurations"
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az vm run-command invoke --resource-group RandRG --name RandVM1 --command-id RunPowerShellScript --scripts "Install-WindowsFeature -Name Web-Server -IncludeManagementTools; Set-Content -Path C:\\inetpub\\wwwroot\\iisstart.htm -Value '<h1>Welcome from RandVM1</h1>'"
{
  "value": [
    {
      "code": "ComponentStatus/StdOut/succeeded",
      "displayStatus": "Provisioning succeeded",
      "level": "Info",
      "message": "Success Restart Needed Exit Code      Feature Result                               \n------- -------------- ---------      --------------                               \nTrue    No             Success        {Common HTTP Features, Default Document, D...\n\n",
      "time": null
    },
    {
      "code": "ComponentStatus/StdErr/succeeded",
      "displayStatus": "Provisioning succeeded",
      "level": "Info",
      "message": "",
      "time": null
    }
  ]
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az vm run-command invoke --resource-group RandRG --name RandVM2 --command-id RunPowerShellScript --scripts "Install-WindowsFeature -Name Web-Server -IncludeManagementTools; Set-Content -Path C:\\inetpub\\wwwroot\\iisstart.htm -Value '<h1>Welcome from RandVM2</h1>'"
{
  "value": [
    {
      "code": "ComponentStatus/StdOut/succeeded",
      "displayStatus": "Provisioning succeeded",
      "level": "Info",
      "message": "Success Restart Needed Exit Code      Feature Result                               \n------- -------------- ---------      --------------                               \nTrue    No             Success        {Common HTTP Features, Default Document, D...\n\n",
      "time": null
    },
    {
      "code": "ComponentStatus/StdErr/succeeded",
      "displayStatus": "Provisioning succeeded",
      "level": "Info",
      "message": "",
      "time": null
    }
  ]
}

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>az network public-ip show --name RandPublicIP --resource-group RandRG --query "ipAddress" --output tsv
52.191.117.191

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>curl http://52.191.117.191
<h1>Welcome from RandVM2</h1>

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>curl http://52.191.117.191
<h1>Welcome from RandVM1</h1>

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>curl http://52.191.117.191
<h1>Welcome from RandVM2</h1>

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>curl http://52.191.117.191
<h1>Welcome from RandVM1</h1>

D:\0Intern\Prof cloud compu devops\COURSES\8. Azure Administrator\Projects>
