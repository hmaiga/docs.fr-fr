---
title: Ressources de formation Azure sur le générateur de modèles
description: Guide des ressources pour Azure Machine Learning
ms.topic: reference
ms.date: 02/25/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a0a75283cdc7402c67b6bfb0799189fa34cd39a7
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77675204"
---
# <a name="model-builder-azure-training-resources"></a><span data-ttu-id="40e4d-103">Ressources de formation Azure sur le générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="40e4d-103">Model Builder Azure Training Resources</span></span>

<span data-ttu-id="40e4d-104">Vous trouverez ci-dessous un guide pour en savoir plus sur les ressources utilisées pour l’apprentissage des modèles dans Azure avec le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="40e4d-104">The following is a guide to help you learn more about resources used to train models in Azure with Model Builder.</span></span>

## <a name="what-is-an-azure-machine-learning-experiment"></a><span data-ttu-id="40e4d-105">Qu’est-ce qu’une expérience Azure Machine Learning ?</span><span class="sxs-lookup"><span data-stu-id="40e4d-105">What is an Azure Machine Learning experiment?</span></span>

<span data-ttu-id="40e4d-106">Une expérience Azure Machine Learning est une ressource qui doit être créée avant l’exécution de la formation du générateur de modèles sur Azure.</span><span class="sxs-lookup"><span data-stu-id="40e4d-106">An Azure Machine Learning experiment is a resource that needs to be created before running Model Builder training on Azure.</span></span>

<span data-ttu-id="40e4d-107">L’expérimentation encapsule la configuration et les résultats d’une ou de plusieurs Machine Learning exécutions d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="40e4d-107">The experiment encapsulates the configuration and results for one or more machine learning training runs.</span></span> <span data-ttu-id="40e4d-108">Les expériences appartiennent à un espace de travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="40e4d-108">Experiments belong to a specific workspace.</span></span> <span data-ttu-id="40e4d-109">La première fois qu’une expérience est créée, son nom est enregistré dans l’espace de travail.</span><span class="sxs-lookup"><span data-stu-id="40e4d-109">The first time an experiment is created, its name is registered in the workspace.</span></span> <span data-ttu-id="40e4d-110">Toutes les exécutions suivantes : si le même nom d’expérimentation est utilisé, sont enregistrés dans le cadre de la même expérience.</span><span class="sxs-lookup"><span data-stu-id="40e4d-110">Any subsequent runs - if the same experiment name is used - are logged as part of the same experiment.</span></span> <span data-ttu-id="40e4d-111">Dans le cas contraire, une nouvelle expérience est créée.</span><span class="sxs-lookup"><span data-stu-id="40e4d-111">Otherwise, a new experiment is created.</span></span>

## <a name="what-is-an-azure-machine-learning-workspace"></a><span data-ttu-id="40e4d-112">Qu’est-ce qu’un espace de travail Azure Machine Learning ?</span><span class="sxs-lookup"><span data-stu-id="40e4d-112">What is an Azure Machine Learning workspace?</span></span>

<span data-ttu-id="40e4d-113">Un espace de travail est une ressource Azure Machine Learning qui fournit un emplacement central pour toutes les ressources Azure Machine Learning et les artefacts créés dans le cadre de l’exécution de la formation.</span><span class="sxs-lookup"><span data-stu-id="40e4d-113">A workspace is an Azure Machine Learning resource that provides a central place for all Azure Machine Learning resources and artifacts created as part of training run.</span></span>

<span data-ttu-id="40e4d-114">Pour créer un espace de travail Azure Machine Learning, les conditions suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="40e4d-114">To create an Azure Machine Learning workspace, the following are required:</span></span>

- <span data-ttu-id="40e4d-115">Nom : un nom pour votre espace de travail entre 3-33 caractères.</span><span class="sxs-lookup"><span data-stu-id="40e4d-115">Name: A name for your workspace between 3-33 characters.</span></span> <span data-ttu-id="40e4d-116">Les noms peuvent uniquement contenir des caractères alphanumériques et des traits d’Union.</span><span class="sxs-lookup"><span data-stu-id="40e4d-116">Names may only contain alphanumeric characters and hyphens.</span></span> 
- <span data-ttu-id="40e4d-117">Région : emplacement géographique du centre de données où votre espace de travail et vos ressources sont déployés.</span><span class="sxs-lookup"><span data-stu-id="40e4d-117">Region: The geographic location of the data center where your workspace and resources are deployed to.</span></span> <span data-ttu-id="40e4d-118">Il est recommandé de choisir un emplacement proche de l’emplacement où se trouvent vos clients ou vous-même.</span><span class="sxs-lookup"><span data-stu-id="40e4d-118">It is recommended that you choose a location close to where you or your customers are.</span></span>
- <span data-ttu-id="40e4d-119">Groupe de ressources : conteneur qui contient toutes les ressources associées d’une solution Azure.</span><span class="sxs-lookup"><span data-stu-id="40e4d-119">Resource group: A container that contains all related resources for an Azure solution.</span></span>

## <a name="what-is-an-azure-machine-learning-compute"></a><span data-ttu-id="40e4d-120">Qu’est-ce qu’un calcul Azure Machine Learning ?</span><span class="sxs-lookup"><span data-stu-id="40e4d-120">What is an Azure Machine Learning compute?</span></span>

<span data-ttu-id="40e4d-121">Une Azure Machine Learning Compute est une machine virtuelle Linux basée sur le Cloud, utilisée pour l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="40e4d-121">An Azure Machine Learning compute is a cloud-based Linux VM used for training.</span></span>

<span data-ttu-id="40e4d-122">Pour créer un espace de travail Azure Machine Learning, les conditions suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="40e4d-122">To create an Azure Machine Learning workspace, the following are required:</span></span>

- <span data-ttu-id="40e4d-123">Nom : un nom pour votre espace de travail entre 2-16 caractères.</span><span class="sxs-lookup"><span data-stu-id="40e4d-123">Name: A name for your workspace between 2-16 characters.</span></span> <span data-ttu-id="40e4d-124">Les noms peuvent uniquement contenir des caractères alphanumériques et des traits d’Union.</span><span class="sxs-lookup"><span data-stu-id="40e4d-124">Names may only contain alphanumeric characters and hyphens.</span></span>
- <span data-ttu-id="40e4d-125">Taille de calcul</span><span class="sxs-lookup"><span data-stu-id="40e4d-125">Compute size</span></span>

    <span data-ttu-id="40e4d-126">Le générateur de modèles peut utiliser l’un des types de calcul optimisés GPU suivants :</span><span class="sxs-lookup"><span data-stu-id="40e4d-126">Model Builder can use one of the following GPU-optimized compute types:</span></span>

    | <span data-ttu-id="40e4d-127">Size</span><span class="sxs-lookup"><span data-stu-id="40e4d-127">Size</span></span> | <span data-ttu-id="40e4d-128">Processeurs virtuels</span><span class="sxs-lookup"><span data-stu-id="40e4d-128">vCPU</span></span> | <span data-ttu-id="40e4d-129">Mémoire : Gio</span><span class="sxs-lookup"><span data-stu-id="40e4d-129">Memory: GiB</span></span> | <span data-ttu-id="40e4d-130">Stockage temporaire (SSD) en Gio</span><span class="sxs-lookup"><span data-stu-id="40e4d-130">Temp storage (SSD) GiB</span></span> | <span data-ttu-id="40e4d-131">GPU</span><span class="sxs-lookup"><span data-stu-id="40e4d-131">GPU</span></span> | <span data-ttu-id="40e4d-132">Mémoire GPU : Gio</span><span class="sxs-lookup"><span data-stu-id="40e4d-132">GPU memory: GiB</span></span> | <span data-ttu-id="40e4d-133">Disques de données max.</span><span class="sxs-lookup"><span data-stu-id="40e4d-133">Max data disks</span></span> | <span data-ttu-id="40e4d-134">Nombre max de cartes réseau</span><span class="sxs-lookup"><span data-stu-id="40e4d-134">Max NICs</span></span> |
    |---|---|---|---|---|---|---|---|
    | <span data-ttu-id="40e4d-135">Standard_NC12</span><span class="sxs-lookup"><span data-stu-id="40e4d-135">Standard_NC12</span></span>   | <span data-ttu-id="40e4d-136">12</span><span class="sxs-lookup"><span data-stu-id="40e4d-136">12</span></span> | <span data-ttu-id="40e4d-137">112</span><span class="sxs-lookup"><span data-stu-id="40e4d-137">112</span></span> | <span data-ttu-id="40e4d-138">680</span><span class="sxs-lookup"><span data-stu-id="40e4d-138">680</span></span>  | <span data-ttu-id="40e4d-139">2</span><span class="sxs-lookup"><span data-stu-id="40e4d-139">2</span></span> | <span data-ttu-id="40e4d-140">24</span><span class="sxs-lookup"><span data-stu-id="40e4d-140">24</span></span> | <span data-ttu-id="40e4d-141">48</span><span class="sxs-lookup"><span data-stu-id="40e4d-141">48</span></span> | <span data-ttu-id="40e4d-142">2</span><span class="sxs-lookup"><span data-stu-id="40e4d-142">2</span></span> |
    | <span data-ttu-id="40e4d-143">Standard_NC24</span><span class="sxs-lookup"><span data-stu-id="40e4d-143">Standard_NC24</span></span>   | <span data-ttu-id="40e4d-144">24</span><span class="sxs-lookup"><span data-stu-id="40e4d-144">24</span></span> | <span data-ttu-id="40e4d-145">224</span><span class="sxs-lookup"><span data-stu-id="40e4d-145">224</span></span> | <span data-ttu-id="40e4d-146">1440</span><span class="sxs-lookup"><span data-stu-id="40e4d-146">1440</span></span> | <span data-ttu-id="40e4d-147">4</span><span class="sxs-lookup"><span data-stu-id="40e4d-147">4</span></span> | <span data-ttu-id="40e4d-148">48</span><span class="sxs-lookup"><span data-stu-id="40e4d-148">48</span></span> | <span data-ttu-id="40e4d-149">64</span><span class="sxs-lookup"><span data-stu-id="40e4d-149">64</span></span> | <span data-ttu-id="40e4d-150">4</span><span class="sxs-lookup"><span data-stu-id="40e4d-150">4</span></span> |

    <span data-ttu-id="40e4d-151">Pour plus d’informations sur les types de calcul optimisés GPU, consultez la documentation sur les [machines virtuelles Linux de série NC](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) .</span><span class="sxs-lookup"><span data-stu-id="40e4d-151">Visit the [NC-series Linux VM documentation](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) for more details on GPU optimized compute types.</span></span>

## <a name="training"></a><span data-ttu-id="40e4d-152">Entrainement</span><span class="sxs-lookup"><span data-stu-id="40e4d-152">Training</span></span>

<span data-ttu-id="40e4d-153">La formation sur Azure est disponible uniquement pour le scénario de classification d’image du générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="40e4d-153">Training on Azure is only available for the Model Builder image classification scenario.</span></span> <span data-ttu-id="40e4d-154">L’algorithme utilisé pour l’apprentissage de ces modèles est un réseau neuronal profond basé sur l’architecture ResNet50.</span><span class="sxs-lookup"><span data-stu-id="40e4d-154">The algorithm used to train these models is a Deep Neural Network based on the ResNet50 architecture.</span></span> <span data-ttu-id="40e4d-155">Pendant la formation, les ressources nécessaires pour former le modèle sont approvisionnées et le modèle est formé.</span><span class="sxs-lookup"><span data-stu-id="40e4d-155">During training, the resources required to train the model are provisioned and the model is trained.</span></span> <span data-ttu-id="40e4d-156">Ce processus prend quelques minutes et la durée peut varier en fonction de la taille du calcul sélectionné et de la quantité de données.</span><span class="sxs-lookup"><span data-stu-id="40e4d-156">This process takes several minutes and the amount of time may vary depending on the size of compute selected as well as amount of data.</span></span> <span data-ttu-id="40e4d-157">Vous pouvez suivre la progression de vos exécutions en sélectionnant le lien « analyser l’exécution actuelle en Portail Azure » dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40e4d-157">You can track the progress of your runs by selecting the "Monitor current run in Azure portal" link in Visual Studio.</span></span>

## <a name="results"></a><span data-ttu-id="40e4d-158">Résultats</span><span class="sxs-lookup"><span data-stu-id="40e4d-158">Results</span></span>

<span data-ttu-id="40e4d-159">Une fois l’apprentissage terminé, deux projets sont ajoutés à votre solution avec les suffixes suivants :</span><span class="sxs-lookup"><span data-stu-id="40e4d-159">Once training is complete, two projects are added to your solution with the following suffixes:</span></span>

- <span data-ttu-id="40e4d-160">*ConsoleApp*: application C# console .net core qui fournit un code de démarrage pour créer le pipeline de prédiction et effectuer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="40e4d-160">*ConsoleApp*: A C# .NET Core console application that provides starter code to build the prediction pipeline and make predictions.</span></span>
- <span data-ttu-id="40e4d-161">*Modèle*: application C# .NET standard qui contient les modèles de données qui définissent le schéma des données de modèle d’entrée et de sortie, ainsi que les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="40e4d-161">*Model*: A C# .NET Standard application that contains the data models that define the schema of input and output model data as well as the following assets:</span></span>

  - <span data-ttu-id="40e4d-162">bestModel. Onnx : version sérialisée du modèle au format ONNX (Open neuronal Network Exchange).</span><span class="sxs-lookup"><span data-stu-id="40e4d-162">bestModel.onnx: A serialized version of the model in Open Neural Network Exchange (ONNX) format.</span></span> <span data-ttu-id="40e4d-163">ONNX est un format Open source pour les modèles AI qui prend en charge l’interopérabilité entre les infrastructures telles que ML.NET, PyTorch et TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="40e4d-163">ONNX is an open source format for AI models that supports interoperability between frameworks like ML.NET, PyTorch and TensorFlow.</span></span>
  - <span data-ttu-id="40e4d-164">bestModelMap. JSON : liste des catégories utilisées lors de l’élaboration de prédictions pour mapper la sortie du modèle à une catégorie de texte.</span><span class="sxs-lookup"><span data-stu-id="40e4d-164">bestModelMap.json: A list of categories used when making predictions to map the model output to a text category.</span></span>
  - <span data-ttu-id="40e4d-165">MLModel. zip : version sérialisée du pipeline de prédiction ML.NET qui utilise la version sérialisée du modèle *bestModel. Onnx* pour effectuer des prédictions et mapper des sorties à l’aide du fichier `bestModelMap.json`.</span><span class="sxs-lookup"><span data-stu-id="40e4d-165">MLModel.zip: A serialized version of the ML.NET prediction pipeline that uses the serialized version of the model *bestModel.onnx* to make predictions and maps outputs using the `bestModelMap.json` file.</span></span>
  
## <a name="troubleshooting"></a><span data-ttu-id="40e4d-166">Dépannage</span><span class="sxs-lookup"><span data-stu-id="40e4d-166">Troubleshooting</span></span>

### <a name="cannot-create-compute"></a><span data-ttu-id="40e4d-167">Impossible de créer le calcul</span><span class="sxs-lookup"><span data-stu-id="40e4d-167">Cannot create compute</span></span>

<span data-ttu-id="40e4d-168">Si une erreur se produit lors de la création de Azure Machine Learning calcul, il se peut que la ressource de calcul existe toujours, dans un état d’erreur.</span><span class="sxs-lookup"><span data-stu-id="40e4d-168">If an error occurs during Azure Machine Learning compute creation, the compute resource may still exist, in an errored state.</span></span> <span data-ttu-id="40e4d-169">Si vous essayez de recréer la ressource de calcul portant le même nom, l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="40e4d-169">If you try to re-create the compute resource with the same name, the operation fails.</span></span> <span data-ttu-id="40e4d-170">Pour corriger cette erreur, vous avez le choix entre plusieurs possibilités :</span><span class="sxs-lookup"><span data-stu-id="40e4d-170">To fix this error, either:</span></span>

* <span data-ttu-id="40e4d-171">Créer le calcul avec un nom différent</span><span class="sxs-lookup"><span data-stu-id="40e4d-171">Create the new compute with a different name</span></span>
* <span data-ttu-id="40e4d-172">Accéder au Portail Azure et supprimer la ressource de calcul d’origine</span><span class="sxs-lookup"><span data-stu-id="40e4d-172">Go to the Azure portal, and remove the original compute resource</span></span>