---
title: StackTrace_SimpleContext
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: 45ae947cda5b4ddadfb10f5b2bdc78a95f031703
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420684"
---
# <a name="stacktrace_simplecontext-structure"></a>StackTrace_SimpleContext
Fournit un contexte simple qui peut être utilisé à la place d'une structure `CONTEXT` complète.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`StackOffset`|Pointeur de pile, ou le pointeur de pile Enter (ESP) sur les plateformes x86.|  
|`FrameOffset`|Décalage de frame ou registre EBP sur les plateformes x86.|  
|`InstructionOffset`|Le pointeur d’instruction, ou le pointeur d’instruction Enter (EIP) sur les plateformes x86.|  
  
## <a name="remarks"></a>Notes  
 Étant donné que les fonctions de trace de pile ne doivent généralement retourner que l’adresse, le décalage de frame et l’adresse de pile, vous pouvez éventuellement utiliser la structure à la `SimpleContext` place d’une structure de grande taille `CONTEXT` .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** SOS_Stacktrace. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
