---
title: -win32manifest (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924674"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (Options du compilateur C#)
Utilisez l’option **-win32manifest** pour spécifier un fichier manifeste d’application Win32 défini par l’utilisateur à incorporer dans le fichier exécutable portable (PE) d’un projet.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Nom et emplacement du fichier manifeste personnalisé.  
  
## <a name="remarks"></a>Notes   
 Par défaut, le compilateur Visual C# incorpore un manifeste d’application qui spécifie le niveau d’exécution requis « asInvoker ». Il crée le manifeste dans le même dossier que celui dans lequel l’exécutable est généré, normalement le dossier bin\Debug ou bin\Release quand vous utilisez Visual Studio. Pour fournir un manifeste personnalisé, par exemple pour spécifier le niveau d’exécution requis « highestAvailable » ou « requireAdministrator », utilisez cette option pour indiquer le nom du fichier.  
  
> [!NOTE]
> Cette option et l’option [-win32res (Options du compilateur C#)](./win32res-compiler-option.md) s’excluent mutuellement. Si vous tentez d’utiliser ces deux options dans la même ligne de commande, une erreur de build se produira.  
  
 Une application sans manifeste d’application pour spécifier le niveau d’exécution requis est soumise à une virtualisation des fichiers/registres sous la fonctionnalité de contrôle de compte d’utilisateur de Windows. Pour plus d’informations, consultez [Contrôle de compte d’utilisateur](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Votre application sera soumise à la virtualisation si l’une de ces conditions est vérifiée :  
  
- Vous utilisez l’option **-nowin32manifest** sans fournir de manifeste au cours d’une étape de génération ultérieure ou en tant que partie du fichier de ressources Windows (.res) à l’aide de l’option **-win32res**.  
  
- Vous fournissez un manifeste personnalisé qui ne spécifie pas le niveau d’exécution requis.  
  
 Visual Studio crée un fichier .manifest par défaut et le stocke dans les répertoires de débogage et de mise en production avec le fichier exécutable. Vous pouvez ajouter un manifeste personnalisé en en créant un dans un éditeur de texte et en ajoutant le fichier au projet. Vous pouvez également cliquer avec le bouton droit sur l’icône **Projet** de l’**Explorateur de solutions**, cliquer sur **Ajouter un nouvel élément**, puis sur **Fichier manifeste d’application**. Une fois que vous avez ajouté votre fichier manifeste nouveau ou existant, il apparaît dans la liste déroulante **Manifeste**. Pour plus d’informations, voir [Page d’application, Concepteur de projets ( CMD).](/visualstudio/ide/reference/application-page-project-designer-csharp)  
  
 Vous pouvez fournir le manifeste d’application en tant qu’étape après génération personnalisée ou en tant que partie d’un fichier de ressources Win32 à l’aide de l’option [-nowin32manifest (Options du compilateur C#)](./nowin32manifest-compiler-option.md). Utilisez cette même option pour que votre application soit soumise à la virtualisation des fichiers ou des registres dans Windows Vista. Cela empêche le compilateur de créer et d’incorporer un manifeste par défaut dans le fichier exécutable portable (PE).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant présente le manifeste par défaut que le compilateur Visual C# insère dans un fichier PE.  
  
> [!NOTE]
> Le compilateur ajoute un nom d’application standard « MyApplication.app » au fichier xml. Cela permet aux applications de s’exécuter dans Windows Server 2003 Service Pack 3.  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
- [-nowin32manifest (Options du compilateur C#)](./nowin32manifest-compiler-option.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
