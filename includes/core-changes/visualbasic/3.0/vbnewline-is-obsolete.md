---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567452"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="9c824-101">Microsoft. VisualBasic. constants. vbNewLine est obsolète</span><span class="sxs-lookup"><span data-stu-id="9c824-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="9c824-102">La constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> est marquée comme [obsolète](xref:System.ObsoleteAttribute) à partir de .net Core 3,0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="9c824-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9c824-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9c824-103">Version introduced</span></span>

<span data-ttu-id="9c824-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="9c824-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="9c824-105">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="9c824-105">Change description</span></span>

<span data-ttu-id="9c824-106">À compter de .NET Core 3,0 Preview 8, l’attribut [Obsolete](xref:System.ObsoleteAttribute) a été appliqué à la constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="9c824-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="9c824-107">L’utilisation de la constante produit un avertissement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="9c824-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="9c824-108">Dans les versions précédentes de .NET Core et .NET Framework, il n’était pas marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="9c824-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="9c824-109">Cette modification a été apportée pour prendre en charge les Visual Basic en tant que langage pour le développement multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="9c824-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="9c824-110">La constante `vbNewLine` est équivalente à `\r\n`, la séquence de caractères de saut de ligne sur Windows.</span><span class="sxs-lookup"><span data-stu-id="9c824-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="9c824-111">Sur les systèmes basés sur UNIX, le caractère de saut de ligne est `\n`.</span><span class="sxs-lookup"><span data-stu-id="9c824-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9c824-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9c824-112">Recommended action</span></span>

<span data-ttu-id="9c824-113">Le message d’attribut [obsolète](xref:System.ObsoleteAttribute) pour `vbNewLine` comprend la recommandation suivante :</span><span class="sxs-lookup"><span data-stu-id="9c824-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="9c824-114">Pour un retour chariot et un saut de ligne, utilisez [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="9c824-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="9c824-115">Pour la nouvelle ligne de la plateforme actuelle, utilisez <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9c824-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="9c824-116">Category</span><span class="sxs-lookup"><span data-stu-id="9c824-116">Category</span></span>

<span data-ttu-id="9c824-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c824-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9c824-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="9c824-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->