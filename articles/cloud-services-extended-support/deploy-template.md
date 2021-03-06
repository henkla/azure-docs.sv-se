---
title: Skapa en Azure Cloud Service (utökad support) – Mallar
description: Skapa en Azure Cloud Service (utökad support) med hjälp av ARM-mallar
ms.topic: tutorial
ms.service: cloud-services-extended-support
author: gachandw
ms.author: gachandw
ms.reviewer: mimckitt
ms.date: 10/13/2020
ms.custom: ''
ms.openlocfilehash: 3b28bc96703fa48e598bfb6f9622237e769119f2
ms.sourcegitcommit: 5cdd0b378d6377b98af71ec8e886098a504f7c33
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757160"
---
# <a name="create-a-cloud-service-extended-support-using-arm-templates"></a>Skapa en moln tjänst (utökad support) med ARM-mallar

I den här självstudien beskrivs hur du skapar en moln tjänst (utökad support) distribution med [arm-mallar](https://docs.microsoft.com/azure/azure-resource-manager/templates/overview). 

> [!IMPORTANT]
> Cloud Services (utökad support) är för närvarande en offentlig för hands version.
> Den här förhandsversionen tillhandahålls utan serviceavtal och rekommenderas inte för produktionsarbetsbelastningar. Vissa funktioner kanske inte stöds eller kan vara begränsade. Mer information finns i [Kompletterande villkor för användning av Microsoft Azure-förhandsversioner](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).


## <a name="before-you-begin"></a>Innan du börjar
1. Granska [distributions kraven](deploy-prerequisite.md) för Cloud Services (utökad support) och skapa de associerade resurserna. 

2. Skapa en ny resurs grupp med hjälp av [Azure Portal](https://docs.microsoft.com/azure/azure-resource-manager/management/manage-resource-groups-portal) eller [PowerShell](https://docs.microsoft.com/azure/azure-resource-manager/management/manage-resource-groups-powershell). Det här steget är valfritt om du använder en befintlig resurs grupp. 
 
3. Skapa ett nytt lagrings konto med hjälp av [Azure Portal](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal) eller [PowerShell](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-powershell). Det här steget är valfritt om du använder ett befintligt lagrings konto. 

4. Överför dina tjänst definitions-(. csdef) och tjänst konfigurations filer (. cscfg) till lagrings kontot med hjälp av [Azure Portal](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal#upload-a-block-blob), [AzCopy](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy-blobs-upload?toc=/azure/storage/blobs/toc.json) eller [PowerShell](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-powershell#upload-blobs-to-the-container). Hämta SAS-URI: er för båda filerna som ska läggas till i ARM-mallen senare i den här självstudien. 

5. Valfritt Skapa ett nyckel valv och ladda upp certifikaten. 
    -  Certifikat kan anslutas till moln tjänster för att möjliggöra säker kommunikation till och från tjänsten. För att kunna använda certifikat måste deras tumavtrycken anges i tjänst konfigurations filen (. cscfg) och överföras till ett nyckel valv. En Key Vault kan skapas via [Azure Portal](https://docs.microsoft.com/azure/key-vault/general/quick-create-portal) eller [PowerShell](https://docs.microsoft.com/azure/key-vault/general/quick-create-powershell). 
    - Den associerade Key Vault måste finnas i samma region och prenumeration som moln tjänsten.   
    - Den associerade Key Vault för måste vara aktive rad, så att Cloud Services (utökad support) resurs kan hämta certifikat från Key Vault. Mer information finns i [certifikat och Key Vault](certificates-and-key-vault.md)
    - Nyckel valvet måste refereras i OsProfile-avsnittet i ARM-mallen som visas i stegen nedan.

## <a name="create-a-cloud-service-extended-support"></a>Skapa en moln tjänst (utökad support) 
1. Skapa virtuellt nätverk. Namnet på det virtuella nätverket måste matcha referenserna i tjänst konfigurations filen (. cscfg). Om du använder ett befintligt virtuellt nätverk utelämnar du det här avsnittet från ARM-mallen.

    ```json
    "resources": [ 
        { 
          "apiVersion": "2019-08-01", 
          "type": "Microsoft.Network/virtualNetworks", 
          "name": "[parameters('vnetName')]", 
          "location": "[parameters('location')]", 
          "properties": { 
            "addressSpace": { 
              "addressPrefixes": [ 
                "10.0.0.0/16" 
              ] 
            }, 
            "subnets": [ 
              { 
                "name": "WebTier", 
                "properties": { 
                  "addressPrefix": "10.0.0.0/24" 
                } 
              } 
            ] 
          } 
        } 
    ] 
    ```
    
     Om du skapar ett nytt virtuellt nätverk lägger du till följande i `dependsOn` avsnittet för att se till att plattformen skapar det virtuella nätverket innan du skapar moln tjänsten. 

    ```json
    "dependsOn": [ 
            "[concat('Microsoft.Network/virtualNetworks/', parameters('vnetName'))]" 
     ] 
    ```
 
2. Skapa en offentlig IP-adress och (valfritt) ange egenskapen DNS-etikett för den offentliga IP-adressen. Om du använder en statisk IP-adress måste du referera till den som en Reserverad IP i tjänst konfigurations filen (. cscfg). Om du använder en befintlig IP-adress hoppar du över det här steget och lägger till information om IP-adressen direkt i konfigurations inställningarna för belastningsutjämnaren i ARM-mallen.
 
    ```json
    "resources": [ 
        { 
          "apiVersion": "2019-08-01", 
          "type": "Microsoft.Network/publicIPAddresses", 
          "name": "[parameters('publicIPName')]", 
          "location": "[parameters('location')]", 
          "properties": { 
            "publicIPAllocationMethod": "Dynamic", 
            "idleTimeoutInMinutes": 10, 
            "publicIPAddressVersion": "IPv4", 
            "dnsSettings": { 
              "domainNameLabel": "[variables('dnsName')]" 
            } 
          }, 
          "sku": { 
            "name": "Basic" 
          } 
        } 
    ] 
    ```
     
     Om du skapar en ny IP-adress lägger du till följande i `dependsOn` avsnittet för att se till att plattformen skapar IP-adressen innan du skapar moln tjänsten. 
    
    ```json
    "dependsOn": [ 
            "[concat('Microsoft.Network/publicIPAddresses/', parameters('publicIPName'))]" 
          ] 
    ```
 
3. Skapa ett nätverks profil objekt och koppla den offentliga IP-adressen till belastningsutjämnarens klient del. En belastningsutjämnare skapas automatiskt av plattformen.  

    ```json
    "networkProfile": { 
        "loadBalancerConfigurations": [ 
          { 
            "id": "[concat(variables('resourcePrefix'), 'Microsoft.Network/loadBalancers/', variables('lbName'))]", 
            "name": "[variables('lbName')]", 
            "properties": { 
              "frontendIPConfigurations": [ 
                { 
                  "name": "[variables('lbFEName')]", 
                  "properties": { 
                    "publicIPAddress": { 
                      "id": "[concat(variables('resourcePrefix'), 'Microsoft.Network/publicIPAddresses/', parameters('publicIPName'))]" 
                    } 
                  } 
                } 
              ] 
            } 
          } 
        ] 
      } 
    ```
 

4. Lägg till nyckel valvs referensen i  `OsProfile`   avsnittet i arm-mallen. Key Vault används för att lagra certifikat som är kopplade till Cloud Services (utökad support). Lägg till certifikaten i Key Vault och referera sedan till certifikatets tumavtrycken i tjänst konfigurations filen (. cscfg). Du måste också aktivera Key Vault för lämpliga behörigheter så att Cloud Services (utökad support) resurs kan hämta certifikat som lagras som hemligheter från Key Vault. Mer information finns i [använda certifikat med Cloud Services (utökad support)](certificates-and-key-vault.md).
     
    ```json
    "osProfile": { 
          "secrets": [ 
            { 
              "sourceVault": { 
                "id": "/subscriptions/{subscription-id}/resourceGroups/{resource-group}/providers/Microsoft.KeyVault/vaults/{keyvault-name}" 
              }, 
              "vaultCertificates": [ 
                { 
                  "certificateUrl": "https://{keyvault-name}.vault.azure.net:443/secrets/ContosoCertificate/{secret-id}" 
                } 
              ] 
            } 
          ] 
        } 
    ```
  
    > [!NOTE]
    > SourceVault är ARM-resurs-ID: t till din Key Vault. Du hittar den här informationen genom att leta upp resurs-ID: t i avsnittet Egenskaper i Key Vault. 
    > - certificateUrl kan hittas genom att navigera till certifikatet i nyckel valvet som är märkt som **hemligt ID**.  
   >  - certificateUrl ska vara i formatet https://{endpoin}/hemligheter/{secretname}/{Secret-ID}

5. Skapa en roll profil. Se till att antalet roller, roll namn, antalet instanser i varje roll och storlek är detsamma i avsnittet tjänst konfiguration (. cscfg), tjänst definition (. csdef) och roll profil i ARM-mallen. 
    
    ```json
    "roleProfile": { 
          "roles": { 
          "value": [ 
            { 
              "name": "WebRole1", 
              "sku": { 
                "name": "Standard_D1_v2", 
                "capacity": "1" 
              } 
            }, 
            { 
              "name": "WorkerRole1", 
              "sku": { 
                "name": "Standard_D1_v2", 
                "capacity": "1" 
              } 
            } 
        }
    }   
    ```

6. Valfritt Skapa en tilläggs profil för att lägga till tillägg i moln tjänsten. I det här exemplet lägger vi till tillägget för fjärr skrivbord och Windows Azure-diagnostik. 
    
    ```json
        "extensionProfile": {
              "extensions": [
                {
                  "name": "RDPExtension",
                  "properties": {
                    "autoUpgradeMinorVersion": true,
                    "publisher": "Microsoft.Windows.Azure.Extensions",
                    "type": "RDP",
                    "typeHandlerVersion": "1.2.1",
                    "settings": "<PublicConfig>\r\n <UserName>[Insert Username]</UserName>\r\n <Expiration>1/21/2022 12:00:00 AM</Expiration>\r\n</PublicConfig>",
                    "protectedSettings": "<PrivateConfig>\r\n <Password>[Insert Password]</Password>\r\n</PrivateConfig>"
                  }
                },
                {
                  "name": "Microsoft.Insights.VMDiagnosticsSettings_WebRole1",
                  "properties": {
                    "autoUpgradeMinorVersion": true,
                    "publisher": "Microsoft.Azure.Diagnostics",
                    "type": "PaaSDiagnostics",
                    "typeHandlerVersion": "1.5",
                    "settings": "[parameters('wadPublicConfig_WebRole1')]",
                    "protectedSettings": "[parameters('wadPrivateConfig_WebRole1')]",
                    "rolesAppliedTo": [
                      "WebRole1"
              ]
            }
          }
        ]
      }

  
    ```    

7. Granska den fullständiga mallen. 

    ```json
    {
      "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
      "contentVersion": "1.0.0.0",
      "parameters": {
        "cloudServiceName": {
          "type": "string",
          "metadata": {
            "description": "Name of the cloud service"
          }
        },
        "location": {
          "type": "string",
          "metadata": {
            "description": "Location of the cloud service"
          }
        },
        "deploymentLabel": {
          "type": "string",
          "metadata": {
            "description": "Label of the deployment"
          }
        },
        "packageSasUri": {
          "type": "securestring",
          "metadata": {
            "description": "SAS Uri of the CSPKG file to deploy"
          }
        },
        "configurationSasUri": {
          "type": "securestring",
          "metadata": {
            "description": "SAS Uri of the service configuration (.cscfg)"
          }
        },
        "roles": {
          "type": "array",
          "metadata": {
            "description": "Roles created in the cloud service application"
          }
        },
        "wadPublicConfig_WebRole1": {
          "type": "string",
          "metadata": {
             "description": "Public configuration of Windows Azure Diagnostics extension"
          }
         },
        "wadPrivateConfig_WebRole1": {
          "type": "securestring",
          "metadata": {
            "description": "Private configuration of Windows Azure Diagnostics extension"
         }
        },
        "vnetName": {
          "type": "string",
          "defaultValue": "[concat(parameters('cloudServiceName'), 'VNet')]",
          "metadata": {
            "description": "Name of vitual network"
          }
        },
        "publicIPName": {
          "type": "string",
          "defaultValue": "contosocsIP",
          "metadata": {
            "description": "Name of public IP address"
          }
        },
        "upgradeMode": {
          "type": "string",
          "defaultValue": "Auto",
          "metadata": {
            "UpgradeMode": "UpgradeMode of the CloudService"
          }
        }
      },
      "variables": {
        "cloudServiceName": "[parameters('cloudServiceName')]",
        "subscriptionID": "[subscription().subscriptionId]",
        "dnsName": "[variables('cloudServiceName')]",
        "lbName": "[concat(variables('cloudServiceName'), 'LB')]",
        "lbFEName": "[concat(variables('cloudServiceName'), 'LBFE')]",
        "resourcePrefix": "[concat('/subscriptions/', variables('subscriptionID'), '/resourceGroups/', resourceGroup().name, '/providers/')]"
      },
      "resources": [
        {
          "apiVersion": "2019-08-01",
          "type": "Microsoft.Network/virtualNetworks",
          "name": "[parameters('vnetName')]",
          "location": "[parameters('location')]",
          "properties": {
            "addressSpace": {
              "addressPrefixes": [
                "10.0.0.0/16"
              ]
            },
            "subnets": [
              {
                "name": "WebTier",
                "properties": {
                  "addressPrefix": "10.0.0.0/24"
                }
              }
            ]
          }
        },
        {
          "apiVersion": "2019-08-01",
          "type": "Microsoft.Network/publicIPAddresses",
          "name": "[parameters('publicIPName')]",
          "location": "[parameters('location')]",
          "properties": {
            "publicIPAllocationMethod": "Dynamic",
            "idleTimeoutInMinutes": 10,
            "publicIPAddressVersion": "IPv4",
            "dnsSettings": {
              "domainNameLabel": "[variables('dnsName')]"
            }
          },
          "sku": {
            "name": "Basic"
          }
        },
        {
          "apiVersion": "2020-10-01-preview",
          "type": "Microsoft.Compute/cloudServices",
          "name": "[variables('cloudServiceName')]",
          "location": "[parameters('location')]",
          "tags": {
            "DeploymentLabel": "[parameters('deploymentLabel')]",
            "DeployFromVisualStudio": "true"
          },
          "dependsOn": [
            "[concat('Microsoft.Network/virtualNetworks/', parameters('vnetName'))]",
            "[concat('Microsoft.Network/publicIPAddresses/', parameters('publicIPName'))]"
          ],
          "properties": {
            "packageUrl": "[parameters('packageSasUri')]",
            "configurationUrl": "[parameters('configurationSasUri')]",
            "upgradeMode": "[parameters('upgradeMode')]",
            "roleProfile": {
              "roles": [
                {
                  "name": "WebRole1",
                  "sku": {
                    "name": "Standard_D1_v2",
                    "capacity": "1"
                  }
                },
                {
                  "name": "WorkerRole1",
                  "sku": {
                    "name": "Standard_D1_v2",
                    "capacity": "1"
                  }
                }
              ]
            },
            "networkProfile": {
              "loadBalancerConfigurations": [
                {
                  "id": "[concat(variables('resourcePrefix'), 'Microsoft.Network/loadBalancers/', variables('lbName'))]",
                  "name": "[variables('lbName')]",
                  "properties": {
                    "frontendIPConfigurations": [
                      {
                        "name": "[variables('lbFEName')]",
                        "properties": {
                          "publicIPAddress": {
                            "id": "[concat(variables('resourcePrefix'), 'Microsoft.Network/publicIPAddresses/', parameters('publicIPName'))]"
                          }
                        }
                      }
                    ]
                  }
                }
              ]
            },
            "osProfile": {
              "secrets": [
                {
                  "sourceVault": {
                    "id": "/subscriptions/{subscription-id}/resourceGroups/{resource-group}/providers/Microsoft.KeyVault/vaults/{keyvault-name}"
                  },
                  "vaultCertificates": [
                    {
                      "certificateUrl": "https://{keyvault-name}.vault.azure.net:443/secrets/ContosoCertificate/{secret-id}"
                    }
                  ]
                }
              ]
            },
        "extensionProfile": {
              "extensions": [
                {
                  "name": "RDPExtension",
                  "properties": {
                    "autoUpgradeMinorVersion": true,
                    "publisher": "Microsoft.Windows.Azure.Extensions",
                    "type": "RDP",
                    "typeHandlerVersion": "1.2.1",
                    "settings": "<PublicConfig>\r\n <UserName>[Insert Username]</UserName>\r\n <Expiration>1/21/2022 12:00:00 AM</Expiration>\r\n</PublicConfig>",
                    "protectedSettings": "<PrivateConfig>\r\n <Password>[Insert Password]</Password>\r\n</PrivateConfig>"
                  }
                },
                {
                  "name": "Microsoft.Insights.VMDiagnosticsSettings_WebRole1",
                  "properties": {
                    "autoUpgradeMinorVersion": true,
                    "publisher": "Microsoft.Azure.Diagnostics",
                    "type": "PaaSDiagnostics",
                    "typeHandlerVersion": "1.5",
                    "settings": "[parameters('wadPublicConfig_WebRole1')]",
                    "protectedSettings": "[parameters('wadPrivateConfig_WebRole1')]",
                    "rolesAppliedTo": [
                      "WebRole1"
                  ]
                }
              }
            ]
          }
        }
      }
    }
    ```
 
8. Distribuera mallen och skapa moln tjänsten (utökad support) distribution. 

    ```powershell
    New-AzResourceGroupDeployment -ResourceGroupName “ContosOrg -TemplateFile "file path to your template file”  
    ```
 
## <a name="next-steps"></a>Nästa steg 
- Läs igenom [vanliga frågor och svar](faq.md) om Cloud Services (utökad support).
- Distribuera en moln tjänst (utökad support) med hjälp av [Azure Portal](deploy-portal.md), [PowerShell](deploy-powershell.md), [mall](deploy-template.md) eller [Visual Studio](deploy-visual-studio.md).
