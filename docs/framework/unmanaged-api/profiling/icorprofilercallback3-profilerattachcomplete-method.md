---
title: ICorProfilerCallback3::ProfilerAttachComplete, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865426"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>ICorProfilerCallback3::ProfilerAttachComplete, méthode
Appelée par le common language runtime (CLR) pour indiquer que le profileur peut désormais appeler les méthodes de rattrapage [ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) et [Icorprofilerinfo3 :: EnumModules](icorprofilerinfo3-enummodules-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>Notes  
 Le rappel `ProfilerAttachComplete` est émis après l’appel de la méthode [ICorProfilerCallback3 :: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) . Il indique ce qui suit :  
  
- Les rappels demandés par le profileur dans `InitializeForAttach` ont été activés.  
  
- Le profileur peut désormais exécuter un rattrapage sur les ID associés sans risquer de manquer des notifications.  
  
 Le CLR ignore la valeur de retour de ce rappel.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerInfo3, interface](icorprofilerinfo3-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
