---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430342"
---
# <a name="mexhttpsbinding"></a>\<mexHttpsBinding >
Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur HTTPS.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**mexHttpsBinding >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`name`|Chaîne qui contient le nom de configuration de la liaison. Cette valeur doit être unique car elle permet d'identifier la liaison. À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`receiveTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:10:00.|  
|`sendTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[liaisons de \<>](bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## <a name="remarks"></a>Notes  
 Cette liaison est essentiellement une liaison `WSHttpBinding` qui prend en charge la sécurité au niveau du transport à l’aide de certificats. Pour plus d’informations sur la configuration et l’utilisation d’un tel point de terminaison de métadonnées, consultez [Comment : configurer une liaison de WS-Metadata Exchange personnalisée](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [Comment : récupérer des métadonnées sur une liaison non MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)et l’exemple de [point de terminaison de métadonnées sécurisé personnalisé](../../../wcf/samples/custom-secure-metadata-endpoint.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [Guide pratique pour publier les métadonnées d’un service à l’aide d’un fichier de configuration](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Publication et récupération de métadonnées sur une liaison personnalisée](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [Guide pratique pour configurer une liaison WS-Metadata Exchange personnalisée](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Guide pratique pour récupérer des métadonnées sur une liaison non-MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [Point de terminaison de métadonnées sécurisé personnalisé](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [Métadonnées](../../../wcf/feature-details/metadata.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [liaison de \<>](bindings.md)
