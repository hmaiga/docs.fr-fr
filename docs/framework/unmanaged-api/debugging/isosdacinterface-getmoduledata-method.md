---
title: ISOSDacInterface::GetModuleData (méthode)
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 80b15f076dfe7a7bbbe7e28d9d68f01255e47202
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828611"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="e24f0-102">ISOSDacInterface::GetModuleData (méthode)</span><span class="sxs-lookup"><span data-stu-id="e24f0-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="e24f0-103">Extrait les données correspondant au module chargé à une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="e24f0-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e24f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e24f0-104">Syntax</span></span>

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

### <a name="parameters"></a><span data-ttu-id="e24f0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e24f0-105">Parameters</span></span>

<span data-ttu-id="e24f0-106">`moduleAddr` [in] L’adresse du module pour récupérer des informations pour.</span><span class="sxs-lookup"><span data-stu-id="e24f0-106">`moduleAddr` [in] The address of the module to retrieve information for.</span></span>

<span data-ttu-id="e24f0-107">`data` [out] Le [DacpModuleData structure](dacpmoduledata-structure.md) pour contenir les informations du module chargé.</span><span class="sxs-lookup"><span data-stu-id="e24f0-107">`data` [out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>


## <a name="remarks"></a><span data-ttu-id="e24f0-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e24f0-108">Remarks</span></span>

<span data-ttu-id="e24f0-109">La méthode fournie fait partie de la `ISOSDacInterface` interface et correspond à l’emplacement de 13 de la table de la méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="e24f0-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e24f0-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e24f0-110">Requirements</span></span>

<span data-ttu-id="e24f0-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e24f0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e24f0-112">**En-tête :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="e24f0-112">**Header:** None</span></span>  
<span data-ttu-id="e24f0-113">**Bibliothèque :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="e24f0-113">**Library:** None</span></span>  
<span data-ttu-id="e24f0-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e24f0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e24f0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e24f0-115">See also</span></span>

- [<span data-ttu-id="e24f0-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="e24f0-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="e24f0-117">Interface de ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="e24f0-117">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)