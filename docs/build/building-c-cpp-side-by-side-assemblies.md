---
title: Génération d’assemblys côte C/C++ côte à côte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51435d0613a7f68ca906058e4ff72f1ad34e6c54
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701582"
---
# <a name="building-cc-side-by-side-assemblies"></a>Génération d'assemblys côte à côte C/C++

Un [côte à côte assembly](/windows/desktop/SbsCs/about-side-by-side-assemblies-) est une collection de ressources, un groupe de DLL, de classes de windows, de serveurs COM, de bibliothèques de types ou d’interfaces, disponibles pour une application à utiliser lors de l’exécution. Le principal avantage de réintégration des DLL dans les assemblys est que plusieurs versions d’assemblys peuvent être utilisées par les applications en même temps, et il est possible d’assemblys de service est actuellement installé dans le cas d’une mise à jour.

Une application Visual C++ peut utiliser une ou plusieurs DLL dans différentes parties de l’application. Lors de l’exécution, les DLL sont chargées dans le processus principal et le code requis est exécuté. L’application s’appuie sur le système d’exploitation pour localiser les DLL demandées, comprendre les autres DLL dépendantes qui doivent être chargés et les charger avec la DLL demandée. Sur les versions de systèmes d’exploitation Windows antérieurs à Windows XP, Windows Server 2003 et Windows Vista, le chargeur du système d’exploitation recherche les DLL dépendantes dans le dossier local de l’application ou un autre dossier spécifié sur le chemin d’accès système. Sous Windows XP, Windows Server 2003 et Windows Vista, le chargeur du système d’exploitation peut également rechercher les DLL dépendantes à l’aide un [manifeste](https://msdn.microsoft.com/library/windows/desktop/aa375365) fichier et recherchez les assemblys côte à côte qui contiennent ces DLL.

Par défaut, lorsqu’une DLL est générée avec Visual Studio, elle a un [manifeste d’application](/windows/desktop/SbsCs/application-manifests) incorporé comme ressource RT_MANIFEST avec l’ID est égal à 2. Comme pour un fichier exécutable, ce manifeste décrit les dépendances de cette DLL avec d’autres assemblys. Cela suppose que la DLL ne fait pas partie d’un assembly côte à côte et les applications qui dépendent de cette DLL ne vont pas utiliser un manifeste d’application à charger, mais reposent plutôt sur le chargeur du système d’exploitation pour rechercher cette DLL dans le chemin d’accès système.

> [!NOTE]
>  Il est important pour une DLL qui utilise un manifeste d’application pour que le manifeste incorporé en tant que ressource avec l’ID est égal à 2. Si la DLL est chargée dynamiquement pendant l’exécution (par exemple, à l’aide de la [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175) fonction), le chargeur du système d’exploitation charge les assemblys dépendants spécifiés dans le manifeste de la DLL. Un manifeste d’application externe pour les DLL n’est pas vérifié pendant un `LoadLibrary` appeler. Si le manifeste n’est pas incorporé, le chargeur peut tenter de charger des versions incorrectes des assemblys ou ne parviennent pas à trouver les assemblys dépendants.

Une ou plusieurs connexes DLL peuvent être réorganisées dans un assembly côte à côte avec un correspondant [manifeste d’assembly](/windows/desktop/SbsCs/assembly-manifests), qui décrit les fichiers l’assembly, ainsi que la dépendance de l’assembly sur les autres côte à côte assemblys.

> [!NOTE]
>  Si un assembly contient une DLL, il est recommandé d’incorporer le manifeste d’assembly dans cette DLL en tant que ressource avec un ID égal à 1 et de donner à l’assembly privé le même nom que la DLL. Par exemple, si le nom de la DLL est mylibrary.dll, la valeur de l’attribut name est utilisée dans le \<assemblyIdentity > élément du manifeste peut être également mylibrary. Dans certains cas, lorsqu’une bibliothèque a une extension autre que .dll (par exemple, un projet de contrôles ActiveX MFC crée une bibliothèque .ocx) un manifeste d’assembly externe peut être créé. Dans ce cas, le nom de l’assembly et son manifeste doit être différent du nom de la DLL (par exemple, MyAssembly, MyAssembly.manifest et mylibrary.ocx). Toutefois il est recommandé de toujours renommer ces bibliothèques pour l’extension.dll et incorporer le manifeste en tant que ressource afin de réduire les coûts de maintenance future de cet assembly. Pour plus d’informations sur la façon dont le système d’exploitation recherche les assemblys privés, consultez [séquence de recherche d’Assembly](/windows/desktop/SbsCs/assembly-searching-sequence).

Cette modification peut permettre de déployer les DLL correspondantes comme un [assembly privé](/windows/desktop/Msi/private-assemblies) dans un dossier local d’application ou comme un [partagé assembly](/windows/desktop/Msi/shared-assemblies) dans le cache d’assembly WinSxS. Plusieurs étapes doivent être suivies pour que le comportement d’exécution correcte de ce nouvel assembly ; ils sont décrits dans [les instructions pour les assemblys côte à côte de création](/windows/desktop/SbsCs/guidelines-for-creating-side-by-side-assemblies). Une fois un assembly correctement créé, il peut déployé comme soit un assembly privé ou partagé avec une application qui en dépend. Lorsque vous installez les assemblys côte à côte comme un assembly partagé, vous pouvez soit suivre les indications de [installation d’assemblys Win32 pour le partage côte à côte sur Windows XP](/windows/desktop/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp) ou utilisez [demodulesdefusion](https://msdn.microsoft.com/library/windows/desktop/aa369820). Lorsque vous installez les assemblys côte à côte comme un assembly privé, vous suffit de copier le manifeste d’assembly, les ressources et les DLL correspondant dans le cadre du processus d’installation dans le dossier local d’application sur l’ordinateur cible, en garantissant que cet assembly peut être trouvé par le chargeur lors de l’exécution (voir [séquence de recherche d’Assembly](/windows/desktop/SbsCs/assembly-searching-sequence)). Une autre méthode consiste à utiliser [programme d’installation de Windows](/windows/desktop/Msi/windows-installer-portal) et suivez les instructions décrites dans [installation d’assemblys Win32 pour l’usage privé d’une Application sur Windows XP](/windows/desktop/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp).

## <a name="see-also"></a>Voir aussi

[Exemples de déploiement](../ide/deployment-examples.md)<br/>
[Génération d’applications isolées C/C++](../build/building-c-cpp-isolated-applications.md)<br/>
[Génération d’applications isolées et d’assemblys côte à côte C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)