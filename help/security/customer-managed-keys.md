---
title: AEM as a Cloud Service용 고객 관리 키
description: AEM as a Cloud Service의 암호화 키를 관리하는 방법 알아보기
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 100ddbf2-9c63-406f-a78d-22862501a085
source-git-commit: 18fe0125351c635c226bebf0f309710634230e64
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 0%

---

# AEM as a Cloud Service용 고객 관리 키 설정 {#cusomer-managed-keys-for-aem-as-a-cloud-service}

AEM as a Cloud Service은 현재 Azure Blob Storage 및 MongoDB에 고객 데이터를 저장하며, 기본적으로 공급자 관리 암호화 키를 사용하여 데이터를 보호합니다. 이러한 설정은 많은 조직의 보안 요구 사항을 충족하지만, 규제 대상 업종의 기업이나 강화된 데이터 주권이 필요한 기업에서는 암호화 방식에 대한 보다 강력한 제어를 요구할 수 있습니다. 데이터 보안, 규정 준수 및 암호화 키 관리 기능에 우선 순위를 두는 조직의 경우 CMK(Customer Managed Keys) 솔루션을 통해 중요한 기능이 향상되었습니다.

## 해결 중인 문제 {#the-problem-being-solved}

공급자 관리 키를 사용하면 엄격한 규정이 데이터 보안에 대한 포괄적인 제어를 요구하는 금융, 의료 및 정부와 같은 분야의 비즈니스에 문제가 발생할 수 있습니다. 주요 관리 업무를 제어하지 않으면 규정 준수 요구 사항 충족, 맞춤형 보안 정책 구현, 완벽한 데이터 주권 확보 등의 과제에 직면하게 됩니다.

CMK(고객 관리 키) 도입은 AEM 고객이 암호화 키를 완전히 제어할 수 있도록 지원함으로써 이러한 우려를 해결합니다. AEM CS는 Microsoft Entra ID(이전의 Azure Active Directory)를 통해 인증함으로써 고객의 Azure Key Vault에 안전하게 연결되므로 암호화 키의 수명 주기를 관리할 수 있습니다. 여기에는 키 생성, 순환 및 해지가 포함됩니다.

CMK는 다음과 같은 몇 가지 이점을 제공합니다.

* **향상된 보안:** 고객은 암호화 방법이 특정 보안 요구 사항을 충족하도록 하여 데이터 보호에 대해 안심할 수 있습니다.
* **규정 준수 유연성:** 주요 라이프사이클을 완벽하게 제어하므로 기업은 GDPR, HIPAA 또는 CCPA와 같이 진화하는 규제 표준에 쉽게 적응하여 규정 준수 태세가 지속적으로 유지될 수 있습니다.
* **원활한 통합:** CMK 솔루션은 AEM CS의 Azure Blob Storage 및 MongoDB와 직접 통합되므로 스토리지 작업을 중단하거나 유용하지 않고 고객에게 강력한 암호화 기능을 제공합니다.

CMK를 채택함으로써 고객은 데이터 보안 및 암호화 관행에 대한 통제력을 높이고 규정 준수를 강화하며 위험을 완화하는 동시에 AEM CS의 확장성과 유연성을 지속적으로 누릴 수 있습니다.

AEM as a Cloud Service을 사용하면 사용하지 않는 데이터를 암호화하기 위한 자체 암호화 키를 가져올 수 있습니다. 이 안내서에서는 AEM as a Cloud Service용 Azure Key Vault에서 CMK(Customer Managed Key)를 설정하는 단계를 제공합니다.

>[!WARNING]
>
>CMK를 설정한 후에는 시스템 관리 키로 되돌릴 수 없습니다. Azure에서 키를 안전하게 관리하고 Key Vault, Key 및 CMK 앱에 대한 액세스 권한을 제공하여 데이터에 대한 액세스 권한을 상실하지 않도록 해야 합니다.

필요한 인프라를 만들고 구성하는 다음 단계도 안내됩니다.

1. 환경 설정
1. Adobe에서 애플리케이션 ID 얻기
1. 새 리소스 그룹 만들기
1. 키 아이콘 만들기
1. 키 아이콘에 대한 Adobe 액세스 권한 부여
1. 암호화 키 만들기

키 저장소 URL, 암호화 키 이름 및 키 저장소에 대한 정보를 Adobe과 공유해야 합니다.

## 환경 설정 {#setup-your-environment}

이 안내서의 유일한 요구 사항은 Azure 명령줄 인터페이스(CLI)입니다. Azure CLI가 아직 설치되지 않은 경우 공식 설치 지침 [여기](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)를 따르십시오.

이 안내서의 나머지 부분을 계속 진행하기 전에 `az login`(으)로 CLI에 로그인하십시오.

>[!NOTE]
>
>이 안내서에서는 Azure CLI를 사용하지만 Azure 콘솔을 통해 동일한 작업을 수행할 수 있습니다. Azure 콘솔을 사용하려면 아래 명령을 참조로 사용하십시오.

## Adobe에서 애플리케이션 ID 얻기 {#obtain-an-application-id-from-adobe}

Adobe은 이 안내서의 나머지 부분에서 필요한 Entra 애플리케이션 ID를 제공합니다. 응용 프로그램 ID가 없는 경우 Adobe에 문의하여 ID를 얻으십시오.

## 새 리소스 그룹 만들기 {#create-a-new-resource-group}

원하는 위치에 새 리소스 그룹을 만듭니다.

```powershell
# Choose a location and a name for the resource group.
$location="<AZURE LOCATION>"
$resourceGroup="<RESOURCE GROUP>"

# Create the resource group.
az group create --location $location --resource-group $resourceGroup
```

이미 리소스 그룹이 있는 경우 언제든지 대신 사용할 수 있습니다. 이 안내서의 나머지 부분에서 리소스 그룹의 위치와 해당 이름은 각각 `$location` 및 `$resourceGroup`(으)로 식별됩니다.

## 주요 자격 증명 모음 만들기 {#create-a-key-vault}

암호화 키를 포함할 키 저장소를 만들어야 합니다. 주요 자격 증명 모음에는 제거 보호 기능이 활성화되어 있어야 합니다. 다른 Azure 서비스에서 사용하지 않는 데이터를 암호화하려면 제거 보호가 필요합니다. Adobe 테넌트가 키 자격 증명 모음에 액세스할 수 있도록 하려면 공용 네트워크 액세스도 사용하도록 설정해야 합니다.

>[!IMPORTANT]
>공개 네트워크 액세스가 비활성화된 Key Vault를 만들면 KeyVault에 대한 네트워크 액세스 권한이 있는 환경(예: KeyVault에 액세스할 수 있는 VM)에서 키 작성이나 순환과 같은 모든 Key Vault 관련 작업을 실행해야 합니다.

```powershell
# Reuse this information from the previous step.
$location="<AZURE LOCATION>"
$resourceGroup="<RESOURCE GROUP>"

# Choose a name for the key vault.
$keyVaultName="<KEY VAULT NAME>"

# Create the key vault.
az keyvault create `
  --location $location `
  --resource-group $resourceGroup `
  --name $keyVaultName `
  --default-action=Deny `
  --enable-purge-protection `
  --enable-rbac-authorization `
  --public-network-access Enabled
```

## Key Vault에 대한 Adobe 액세스 권한 부여 {#grant-adone-access-to-the-key-vault}

이 단계에서는 Adobe이 Entra 애플리케이션을 통해 주요 자격 증명 모음에 액세스할 수 있도록 허용합니다. Entra 애플리케이션의 ID는 Adobe에서 이미 제공했어야 합니다.

먼저 Entra 애플리케이션에 연결된 서비스 사용자를 만들고 **Key Vault Reader** 및 **Key Vault 암호화 사용자** 역할을 할당해야 합니다. 역할은 이 안내서에서 만든 주요 자격 증명 모음으로 제한됩니다.

```powershell
# Reuse this information from the previous steps.
$resourceGroup="<RESOURCE GROUP>"
$keyVaultName="<KEY VAULT NAME>"

# The application ID is provided by Adobe.
$appId="<APPLICATION ID>"

# Retrieve the ID of the key vault.
$keyVaultId=(az keyvault show --resource-group $resourceGroup --name $keyVaultName --query id --output tsv)

# Create a new service principal.
$servicePrincipalId=(az ad sp create --id $appId --query id --out tsv)

# Assign the roles to the service principal.
az role assignment create --assignee $servicePrincipalId --role "Key Vault Reader" --scope $keyVaultId
az role assignment create --assignee $servicePrincipalId --role "Key Vault Crypto User" --scope $keyVaultId
```

## 암호화 키 만들기 {#create-an-ecryption-key}

마지막으로 키 저장소에서 암호화 키를 만들 수 있습니다. 이 단계를 완료하려면 **Key Vault 암호화 책임자** 역할이 필요합니다. 로그인한 사용자에게 이 역할이 없는 경우 시스템 관리자에게 문의하여 이 역할을 부여받거나 이미 해당 역할이 있는 사람에게 이 단계를 완료할 것을 요청하십시오.

암호화 키를 만들려면 키 보관소에 대한 네트워크 액세스가 필요합니다. 먼저 키 자격 증명 모음에 액세스할 수 있는지 확인하고 키를 계속 작성합니다.

```powershell
# Reuse this information from the previous steps.
$keyVaultName="<KEY VAULT NAME>"

# Chose a name for your key.
$keyName="<KEY NAME>"

# Create the key.
az keyvault key create --vault-name $keyVaultName --name $keyName
```

## 주요 자격 증명 모음 정보 공유 {#share-the-key-vault-information}

이제 모든 준비가 완료되었습니다. 필요한 정보를 Adobe과 공유하면 됩니다. 이 사용자가 환경 구성을 대신 처리하게 됩니다.

```powershell
# Reuse this information from the previous steps.
$resourceGroup="<RESOURCE GROUP>"
$keyVaultName="<KEY VAULT NAME>"

# Retrieve the URL of your key vault.
$keyVaultUri=(az keyvault show --name $keyVaultName `
    --resource-group $resourceGroup `
    --query properties.vaultUri `
    --output tsv)

# In addition we would need the tenantId and the subscriptionId in order to setup the connection.
$tenantId=(az keyvault show --name $keyVaultName `
    --resource-group $resourceGroup `
    --query properties.tenantId `
    --output tsv)
$subscriptionId="<Subscription ID>"
```


## 키 액세스 취소의 의미 {#implications-of-revoking-key-access}

Key Vault, 키 또는 CMK 앱에 대한 액세스를 취소하거나 비활성화하면 플랫폼 작업에 대한 변경 내용 중지를 포함하여 심각한 차질이 발생할 수 있습니다. 이러한 키가 비활성화되면 Platform의 데이터에 액세스할 수 없게 되고 이 데이터를 사용하는 다운스트림 작업이 중단됩니다. 주요 구성을 변경하기 전에 다운스트림 영향을 완전히 이해하는 것이 중요합니다.

데이터에 대한 Platform 액세스를 취소하기로 결정한 경우 Azure 내의 Key Vault에서 애플리케이션과 연결된 사용자 역할을 제거하여 취소할 수 있습니다.

## 다음 단계 {#next-steps}

연락처 Adobe 및 공유:

* 주요 자격 증명 모음의 URL. 이 단계에서 검색하고 `$keyVaultUri` 변수에 저장했습니다.
* 암호화 키의 이름입니다. 이전 단계에서 키를 만들어 `$keyName` 변수에 저장했습니다.
* 키 자격 증명 모음에 대한 연결을 설정하는 데 필요한 `$resourceGroup`, `$subscriptionId` 및 `$tenantId`입니다.

<!-- Alexandru: hiding this for now

### Private Link Approvals {#private-link-approvals}

>[!TIP]
>You can also consult the [Azure Documentation](https://learn.microsoft.com/en-us/azure/key-vault/general/private-link-service?tabs=portal#how-to-manage-a-private-endpoint-connection-to-key-vault-using-the-azure-portal) on how to approve a Private Endpoint Connection.

Afterwards, an Adobe Engineer assigned to you will contact you to confirm the creation of the private endpoints, and will request you to approve a set of required Connection Requests. The requests can be approved either using the Azure Portal UI, where you can go to **KeyVault > Settings > Networking > Private Endpoint Connections** and approve the requests with names similar to these: 

`mongodb-atlas-<REGION>-<NUMBER>`, `storage-account-private-endpoint` and `backup-storage-account-private-endpoint`. 

Notify the Adobe Engineer once this process is complete and the Private Endpoints show up as **Approved**. -->

## Private Beta의 고객 관리 키 {#customer-managed-keys-in-private-beta}

Adobe의 엔지니어링 팀은 현재 Azure의 개인 링크를 활용하는 CMK의 향상된 구현을 위해 노력하고 있습니다. 새 구현에서는 Adobe 테넌트와 키 자격 증명 모음 간의 직접 개인 링크 연결 덕분에 Azure 백본을 통해 키를 공유할 수 있습니다.

이 향상된 구현은 현재 Private Beta에 있으며 Private Beta 프로그램 구독과 Adobe 엔지니어링과 긴밀히 협력하는 데 동의한 선택한 고객을 위해 활성화할 수 있습니다. 개인 링크를 사용하는 CMK용 Private Beta에 관심이 있는 경우, 자세한 내용은 Adobe에 문의하십시오.
