---
title: ResolveTypeLib, méthode
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
ms.openlocfilehash: f0f6fe321f4d38129b6d70ce94a7ea8de8fff6c8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935670"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib, méthode
Résout le nom simple d’une bibliothèque de types en retournant son chemin d’accès qualifié complet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a>Parameters  
 `bstrSimpleName`  
 dans [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) qui contient le nom simple de la bibliothèque de types.  
  
 `tlbid`  
 dans GUID affecté à la bibliothèque de types dans le registre.  
  
 `lcid`  
 dans ID de localisation de la bibliothèque de types.  
  
 `wMajorVersion`  
 dans Numéro de version principale de la bibliothèque de types. Par exemple, pour la version *x. y*, le numéro de version principale est *x*.  
  
 `wMinorVersion`  
 dans Numéro de version mineure de la bibliothèque de types. Par exemple, pour la version *x. y*, le numéro de version mineure est *y*.  
  
 `syskind`  
 dans Indicateur [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) qui identifie l’environnement d’exploitation. Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 à Pointeur vers un [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) qui contient le chemin d’accès complet de la bibliothèque de types nommée dans le paramètre `bstrSimpleName`.  
  
## <a name="remarks"></a>Notes  
 La méthode `ResolveTypeLib` est appelée par la [fonction LoadTypeLibWithResolver,](loadtypelibwithresolver-function.md) pendant le traitement [de Tlbexp. exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md) .  
  
 Les implémentations personnalisées de cette interface doivent retourner un [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) qui contient le chemin d’accès complet de la bibliothèque de types nommée dans le paramètre `bstrSimpleName`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** TlbRef. idl, TlbRef. h  
  
 **Bibliothèque :** TlbRef. lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’assistance Tlbexp](index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
