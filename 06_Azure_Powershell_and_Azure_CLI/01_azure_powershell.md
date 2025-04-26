# ⚡ Azure PowerShell

---

## 📌 What is Azure PowerShell?

- A **command-line tool** and **scripting environment** for managing Azure resources.
- Built on top of **PowerShell** with **Azure-specific modules** (`Az` module).
- Supports both **Windows** and **cross-platform** (Linux, Mac) via PowerShell Core.

---

## 📥 Installing Azure PowerShell

- Install the latest **Az module**:
  
  ```powershell
  Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
  ```

- Update Az module:
  ```powershell
  Update-Module -Name Az
  ```

- Import Az module if needed:
  ```powershell
  Import-Module Az
  ```

---

## 🔐 Authenticating to Azure

- Sign in to Azure account:
  
  ```powershell
  Connect-AzAccount
  ```

- View subscriptions:
  ```powershell
  Get-AzSubscription
  ```

- Set active subscription:
  ```powershell
  Set-AzContext -SubscriptionId "<your-subscription-id>"
  ```

---


## 🛠️ Common Azure Resource Management Commands

| **Action**                  | **Command Example** |
|-------------------------------|----------------------|
| Create a Resource Group       | `New-AzResourceGroup -Name "rg-demo" -Location "EastUS"` |
| Deploy a Virtual Machine      | `New-AzVM -ResourceGroupName "rg-demo" -Name "vm-demo"` |
| List all Resource Groups      | `Get-AzResourceGroup` |
| Delete a Resource Group       | `Remove-AzResourceGroup -Name "rg-demo"` |
| View All Resources            | `Get-AzResource` |
| Tag a Resource                | `Set-AzResource -ResourceId <id> -Tag @{Environment="Dev"}` |

---

## 🧱 Create a Virtual Network

```powershell
$resourceGroupName="staging-grp"
$location="North Europe"
$networkName="app-network"
$addressPrefix="10.0.0.0/16"

New-AzVirtualNetwork -Name $networkName -ResourceGroupName $resourceGroupName -Location $location -AddressPrefix $addressPrefix
```

## 🧱 View Virtual Network Details

```powershell
$resourceGroupName="staging-grp"
$networkName="app-network"

Get-AzVirtualNetwork -Name $networkName -ResourceGroupName $resourceGroupName
```

---

## 🧱 Add Subnet to an Existing Virtual Network

```powershell
$resourceGroupName="staging-grp"
$networkName="app-network"
$subnetName="SubnetA"
$subnetAddressPrefix="10.0.0.0/24"

$VirtualNetwork = Get-AzVirtualNetwork -Name $networkName -ResourceGroupName $resourceGroupName

Add-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $VirtualNetwork -AddressPrefix $subnetAddressPrefix

$VirtualNetwork | Set-AzVirtualNetwork
```

---

## 🧱 Create a New Virtual Network with a Subnet

```powershell
$resourceGroupName="staging-grp"
$networkName="app-network"
$subnetName="SubnetA"
$subnetAddressPrefix="10.0.0.0/24"
$addressPrefix="10.0.0.0/16"
$location="North Europe"

$subnet=New-AzVirtualNetworkSubnetConfig -Name $subnetName -AddressPrefix $subnetAddressPrefix

New-AzVirtualNetwork -Name $networkName -ResourceGroupName $resourceGroupName -Location $location -AddressPrefix $addressPrefix -Subnet $subnet
```

---

## 🧱 Create a Network Interface

```powershell
$resourceGroupName="staging-grp"
$networkName="app-network"
$subnetName="SubnetA"
$networkInterfaceName="app-interface"

$VirtualNetwork = Get-AzVirtualNetwork -Name $networkName -ResourceGroupName $resourceGroupName

$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $VirtualNetwork -Name $subnetName

New-AzNetworkInterface -Name $networkInterfaceName -ResourceGroupName $resourceGroupName -Location $location -SubnetId $subnet.Id -IpConfigurationName "IpConfig"
```

---

## 🧱 Create a Public IP Address

```powershell
$resourceGroupName="staging-grp"
$location="North Europe"
$publicIPAddressName="app-ip"

New-AzPublicIpAddress -Name $publicIPAddressName -ResourceGroupName $resourceGroupName -Location $location -AllocationMethod Static
```

---
## 🧱 Create a Network Security Group

```powershell
$resourceGroupName="staging-grp"
$location="North Europe"
$networkSecurityGroupName="app-nsg"

$nsgRule1=New-AzNetworkSecurityRuleConfig -Name "Allow-RDP" -Access Allow -Protocol Tcp -Direction Inbound -Priority 120 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix 10.0.0.0/24 -DestinationPortRange 3389

$nsgRule2=New-AzNetworkSecurityRuleConfig -Name "Allow-HTTP" -Access Allow -Protocol Tcp -Direction Inbound -Priority 130 -SourceAddressPrefix Internet -SourcePortRange * `
-DestinationAddressPrefix 10.0.0.0/24 -DestinationPortRange 80

New-AzNetworkSecurityGroup -Name $networkSecurityGroupName -ResourceGroupName $resourceGroupName -Location $location -SecurityRules $nsgRule1,$nsgRule2
```

---
## 🧱 Add a disk to a Virtual Machine

```powershell
$vmName="appvm"
$resourceGroupName="staging-grp"
$diskName="datadisk01"

$vm=Get-AzVM -ResourceGroupName $resourceGroupName -Name $vmName

$vm | Add-AzVMDataDisk -Name $diskName -DiskSizeInGB 16 -CreateOption Empty -Lun 0

$vm | Update-AzVM
```

---
## 🧱 Complete script to create VM and other required resources

```powershell
# Set basic variables for resource group, network, subnet, location
$resourceGroupName = "staging-grp"
$networkName = "app-network"
$subnetName = "SubnetA"
$subnetAddressPrefix = "10.0.0.0/24"
$addressPrefix = "10.0.0.0/16"
$location = "North Europe"

# Create a subnet configuration
$subnet = New-AzVirtualNetworkSubnetConfig -Name $subnetName -AddressPrefix $subnetAddressPrefix

# Create a Virtual Network with the subnet
New-AzVirtualNetwork -Name $networkName -ResourceGroupName $resourceGroupName -Location $location -AddressPrefix $addressPrefix -Subnet $subnet

# Create a static Public IP Address
$publicIPAddressName = "app-ip"
$publicAddress = New-AzPublicIpAddress -Name $publicIPAddressName -ResourceGroupName $resourceGroupName -Location $location -AllocationMethod Static

# Create a Network Interface Card (NIC)
$networkInterfaceName = "app-interface"
$VirtualNetwork = Get-AzVirtualNetwork -Name $networkName -ResourceGroupName $resourceGroupName
$subnet = Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $VirtualNetwork -Name $subnetName

$networkInterface = New-AzNetworkInterface -Name $networkInterfaceName -ResourceGroupName $resourceGroupName -Location $location -SubnetId $subnet.Id -IpConfigurationName "IpConfig"

# Attach the public IP to the NIC
$ipConfig = Get-AzNetworkInterfaceIpConfig -NetworkInterface $networkInterface
$networkInterface | Set-AzNetworkInterfaceIpConfig -PublicIpAddress $publicAddress -Name $ipConfig.Name
$networkInterface | Set-AzNetworkInterface

# Create a Network Security Group (NSG) and add rules
$networkSecurityGroupName = "app-nsg"

# Allow RDP (port 3389) from Internet
$nsgRule1 = New-AzNetworkSecurityRuleConfig -Name "Allow-RDP" -Access Allow -Protocol Tcp -Direction Inbound -Priority 120 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix 10.0.0.0/24 -DestinationPortRange 3389

# Allow HTTP (port 80) from Internet
$nsgRule2 = New-AzNetworkSecurityRuleConfig -Name "Allow-HTTP" -Access Allow -Protocol Tcp -Direction Inbound -Priority 130 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix 10.0.0.0/24 -DestinationPortRange 80

# Create the NSG with above rules
$networkSecurityGroup = New-AzNetworkSecurityGroup -Name $networkSecurityGroupName -ResourceGroupName $resourceGroupName -Location $location -SecurityRules $nsgRule1, $nsgRule2

# Associate the NSG with the Subnet
Set-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $VirtualNetwork -NetworkSecurityGroup $networkSecurityGroup -AddressPrefix $subnetAddressPrefix
$VirtualNetwork | Set-AzVirtualNetwork

# Create an Availability Set for high availability of VMs
$availabilitySetName = "app-set"
$availabilitySet = New-AzAvailabilitySet -Location $location -ResourceGroupName $resourceGroupName -Name $availabilitySetName -Sku aligned -PlatformFaultDomainCount 2 -PlatformUpdateDomainCount 5

# Define a VM configuration
$vmName = "appvm"
$vmSize = "Standard_DS2_v2"
$vmConfig = New-AzVMConfig -Name $vmName -VMSize $vmSize -AvailabilitySetId $availabilitySet.Id

# Provide Admin Credentials
$Credential = Get-Credential

# Configure the Operating System for VM
Set-AzVMOperatingSystem -VM $vmConfig -Credential $Credential -Windows -ComputerName $vmName

# Select Windows Server 2022 Datacenter image from Azure Marketplace
Set-AzVMSourceImage -VM $vmConfig -PublisherName "MicrosoftWindowsServer" `
-Offer "WindowsServer" -Skus "2022-Datacenter" -Version "latest"

# Attach the NIC to the VM
$networkInterfaceName = "app-interface"
$networkInterface = Get-AzNetworkInterface -Name $networkInterfaceName -ResourceGroupName $resourceGroupName
$vm = Add-AzVMNetworkInterface -VM $vmConfig -Id $networkInterface.Id

# Create the Virtual Machine
New-AzVM -ResourceGroupName $resourceGroupName -Location $location -VM $vm

```

---
## 🧱 Create a Storage Account

```powershell
$resourceGroupName="staging-grp"
$location="North Europe"
$storageAccountName="appstore443554554"
$storageAccountKind="StorageV2"
$accountSku="Standard_LRS"

New-AzStorageAccount -ResourceGroupName $resourceGroupName -Name $storageAccountName -Location $location -Kind $storageAccountKind -SkuName $accountSku
```

---
## 🧱 Create a Web App

```powershell
$resourceGroupName="staging-grp"
$location="North Europe"
$appServicePlan="webplan100203"
$appServiceName="webapp6677588383"

New-AzAppServicePlan -ResourceGroupName $resourceGroupName -Location $location -Name $appServicePlan -Tier "F1"

New-AzWebApp -ResourceGroupName $resourceGroupName -Location $location -Name $appServiceName -AppServicePlan $appServicePlan
```

---


# 🧠 Exam Tips

- Know basic **Az module commands** like creating resource groups, VMs, NICs, tagging, and deleting.
- Understand how to **authenticate** and **set the active subscription**.
- **Azure PowerShell** can be used inside **Azure Cloud Shell** (no local install needed).
- **Cloud Shell** automatically has the **Az module installed**.
- You may see questions where **CLI vs PowerShell** commands are compared — **recognize the syntax differences**!

