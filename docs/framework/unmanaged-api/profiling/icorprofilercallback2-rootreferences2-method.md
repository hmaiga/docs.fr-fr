---
title: ICorProfilerCallback2::RootReferences2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: a9ce9a7a56847efcadf09924ffc56c41f20a1c58
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865725"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2, méthode
Notifie le profileur des références racines après qu’un garbage collection s’est produit. Cette méthode est une extension de la méthode [ICorProfilerCallback :: RootReferences](icorprofilercallback-rootreferences-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parameters  
 `cRootRefs`  
 dans Nombre d’éléments dans les tableaux `rootRefIds`, `rootKinds`, `rootFlags`et `rootIds`.  
  
 `rootRefIds`  
 dans Tableau d’ID d’objet, chacun d’entre eux référençant un objet statique ou un objet sur la pile. Les éléments du tableau `rootKinds` fournissent des informations pour classer les éléments correspondants dans le tableau `rootRefIds`.  
  
 `rootKinds`  
 dans Tableau de valeurs [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) qui indiquent le type de la racine garbage collection.  
  
 `rootFlags`  
 dans Tableau de valeurs [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) qui décrivent les propriétés d’une racine garbage collection.  
  
 `rootIds`  
 dans Tableau de valeurs UINT_PTR qui pointent vers un entier qui contient des informations supplémentaires sur la racine garbage collection, en fonction de la valeur du paramètre `rootKinds`.  
  
 Si le type de la racine est une pile, l’ID racine est pour la fonction qui contient la variable. Si cet ID racine est égal à 0, la fonction est une fonction sans nom qui est interne au CLR. Si le type de la racine est un handle, l’ID racine est pour le handle garbage collection. Pour les autres types racine, l’ID est une valeur opaque et doit être ignoré.  
  
## <a name="remarks"></a>Notes  
 Les tableaux `rootRefIds`, `rootKinds`, `rootFlags`et `rootIds` sont des tableaux parallèles. Autrement dit, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`et `rootIds[i]` concernent la même racine.  
  
 `RootReferences` et `RootReferences2` sont appelés pour avertir le profileur. Les profileurs implémentent normalement une méthode ou l’autre, mais pas les deux, car les informations transmises `RootReferences2` sont un sur-ensemble de celles passées dans `RootReferences`.  
  
 Il est possible que les entrées de `rootRefIds` soient égales à zéro, ce qui signifie que la référence racine correspondante est null et ne fait pas référence à un objet sur le tas managé.  
  
 Les ID d’objet retournés par `RootReferences2` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être en train de déplacer des objets d’anciennes adresses vers de nouvelles adresses. Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `RootReferences2`. Quand [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) est appelé, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés en toute sécurité.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)
