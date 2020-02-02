---
title: Installer .NET Core sur Ubuntu 19,10 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Ubuntu 19,10.
author: thraka
ms.author: adegeo
ms.date: 01/16/2020
ms.openlocfilehash: b8fec2afa6f03e3dabbf1ff449431759087163ba
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920642"
---
# <a name="ubuntu-1910-package-manager---install-net-core"></a><span data-ttu-id="88af9-103">Gestionnaire de package Ubuntu 19,10-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="88af9-103">Ubuntu 19.10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="88af9-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Ubuntu 19,10.</span><span class="sxs-lookup"><span data-stu-id="88af9-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.10.</span></span> <span data-ttu-id="88af9-105">Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="88af9-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="88af9-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="88af9-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="88af9-107">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="88af9-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="88af9-108">Enregistrez la clé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="88af9-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="88af9-109">Enregistrez le dépôt du produit.</span><span class="sxs-lookup"><span data-stu-id="88af9-109">Register the product repository.</span></span>
- <span data-ttu-id="88af9-110">Installez les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="88af9-110">Install required dependencies.</span></span>

<span data-ttu-id="88af9-111">Cette opération ne doit être effectuée qu’une fois par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="88af9-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="88af9-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="88af9-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="88af9-113">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="88af9-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="88af9-114">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88af9-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="88af9-115">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="88af9-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="88af9-116">Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-SDK-3,1**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="88af9-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="88af9-117">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="88af9-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="88af9-118">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="88af9-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="88af9-119">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="88af9-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="88af9-120">Si vous recevez un message d’erreur semblable à **incapable de localiser le package aspnetcore-Runtime-3,1**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="88af9-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="88af9-121">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="88af9-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="88af9-122">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88af9-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="88af9-123">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="88af9-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="88af9-124">Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-Runtime-3,1**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="88af9-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="88af9-125">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="88af9-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="88af9-126">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="88af9-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="88af9-127">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88af9-127">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="88af9-128">Impossible de localiser</span><span class="sxs-lookup"><span data-stu-id="88af9-128">Unable to locate</span></span>

<span data-ttu-id="88af9-129">Si vous recevez un message d’erreur semblable à **incapable de localiser le package {le package .net Core}** , exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="88af9-129">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="88af9-130">Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="88af9-130">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="88af9-131">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="88af9-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]