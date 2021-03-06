---
title: 'Atténuation : X509CertificateClaimSet.FindClaims, méthode'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 0b306960c4f11bb6f54aecaeb13297e7725e16a8
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102643"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Atténuation : X509CertificateClaimSet.FindClaims, méthode

En commençant par les applications qui ciblent .NET <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Framework 4.6.1, la méthode tentera de faire correspondre l’argument `claimType` avec toutes les entrées DNS dans son champ SAN.  
  
## <a name="impact"></a>Impact  
 Ce changement affecte uniquement les applications qui ciblent .NET Framework 4.6.1 et versions ultérieures.  
  
 Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de faire correspondre l’argument `claimType` uniquement avec la dernière entrée DNS.  
  
## <a name="mitigation"></a>Limitation des risques  
 Si cette modification n’est pas souhaitable, les applications qui ciblent les versions du cadre .NET en commençant par le cadre [ \<](../configure-apps/file-schema/runtime/runtime-element.md) .NET 4.6.1 peuvent s’en retirer en ajoutant le paramètre de configuration suivant à la section>de l’application :  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 En outre, les applications qui ciblent les versions précédentes du cadre .NET mais sont en cours d’exécution sous le cadre .NET 4.6.1 et les versions ultérieures peuvent opter pour ce comportement en ajoutant le paramètre de configuration suivant à la [ \<section de temps d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
