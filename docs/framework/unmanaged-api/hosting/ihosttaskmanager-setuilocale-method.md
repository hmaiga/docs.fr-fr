---
title: IHostTaskManager::SetUILocale, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: a929a125fc8c70744246f4f96d8a09a4605f537c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132942"
---
# <a name="ihosttaskmanagersetuilocale-method"></a>IHostTaskManager::SetUILocale, méthode
Avertit l’hôte que le common language runtime (CLR) a modifié les paramètres régionaux de l’interface utilisateur (IU), ou culture, sur la tâche en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `lcid`  
 dans Valeur de l’identificateur de paramètres régionaux qui correspond à la culture géographique et à la langue qui viennent d’être attribuées.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetUILocale` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|L’hôte n’autorise pas le code utilisateur managé à modifier la culture de l’interface utilisateur.|  
  
## <a name="remarks"></a>Notes  
 Le runtime appelle `SetUILocale` lorsque la valeur de la propriété <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> est modifiée par le code managé. Cette méthode permet à l’hôte d’exécuter tous les mécanismes qu’il peut avoir pour la synchronisation des paramètres régionaux. Si un hôte n’autorise pas la modification des paramètres régionaux de l’interface utilisateur à partir du code managé, ou n’implémente pas de mécanisme pour synchroniser les paramètres régionaux, il doit retourner E_NOTIMPL à partir de cette méthode.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [SetLocale, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
