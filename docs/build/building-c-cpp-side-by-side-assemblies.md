---
title: Génération d'assemblys côte à côte C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 6e49ba72a397efb97437a2f7e6d721c782875c48
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493327"
---
# <a name="building-cc-side-by-side-assemblies"></a>Génération d'assemblys côte à côte C/C++

Un [assembly côte à côte](/windows/win32/SbsCs/about-side-by-side-assemblies-) est une collection de ressources (un groupe de dll, de classes Windows, de serveurs com, de bibliothèques de types ou d’interfaces) disponible pour une application à utiliser au moment de l’exécution. Le principal avantage du reconditionnement des dll dans les assemblys est que plusieurs versions d’assemblys peuvent être utilisées par les applications en même temps et qu’il est possible de traiter les assemblys actuellement installés dans le cas d’une version de mise à jour.

Une application C++ peut utiliser une ou plusieurs dll dans différentes parties de l’application. Au moment de l’exécution, les dll sont chargées dans le processus principal et le code requis est exécuté. L’application s’appuie sur le système d’exploitation pour localiser les dll demandées, comprendre ce que les autres dll dépendantes doivent être chargées, puis les charger avec la DLL demandée. Sur les versions des systèmes d’exploitation Windows antérieures à Windows XP, Windows Server 2003 et Windows Vista, le chargeur du système d’exploitation recherche les dll dépendantes dans le dossier local de l’application ou dans un autre dossier spécifié sur le chemin d’accès système. Sur Windows XP, Windows Server 2003 et Windows Vista, le chargeur du système d’exploitation peut également rechercher des dll dépendantes à l’aide d’un fichier [manifeste](/windows/win32/sbscs/manifests) et rechercher les assemblys côte à côte qui contiennent ces dll.

Par défaut, lorsqu’une DLL est générée avec Visual Studio, un manifeste d' [application](/windows/win32/SbsCs/application-manifests) est incorporé en tant que ressource de RT_MANIFEST avec l’ID égal à 2. Tout comme pour un fichier exécutable, ce manifeste décrit les dépendances de cette DLL sur d’autres assemblys. Cela suppose que la DLL ne fait pas partie d’un assembly côte à côte et que les applications qui dépendent de cette DLL ne vont pas utiliser un manifeste d’application pour le charger, mais qu’elle s’appuie plutôt sur le chargeur du système d’exploitation pour trouver cette DLL sur le chemin d’accès système.

> [!NOTE]
> Il est important pour une DLL qui utilise un manifeste d’application de faire en sorte que le manifeste soit incorporé en tant que ressource dont l’ID est égal à 2. Si la DLL est chargée dynamiquement au moment de l’exécution (par exemple, à l’aide de la fonction [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) ), le chargeur du système d’exploitation charge les assemblys dépendants spécifiés dans le manifeste de la dll. Un manifeste d’application externe pour les dll n’est pas `LoadLibrary` vérifié pendant un appel. Si le manifeste n’est pas incorporé, le chargeur peut tenter de charger des versions incorrectes des assemblys ou ne parvient pas à trouver les assemblys dépendants.

Une ou plusieurs dll associées peuvent être reconditionnées dans un assembly côte à côte avec un manifeste d' [assembly](/windows/win32/SbsCs/assembly-manifests)correspondant, qui décrit les fichiers de l’assembly ainsi que la dépendance de l’assembly par rapport à d’autres assemblys côte à côte.

> [!NOTE]
> Si un assembly contient une DLL, il est recommandé d’incorporer le manifeste de l’assembly dans cette DLL en tant que ressource dont l’ID est égal à 1, et d’attribuer à l’assembly privé le même nom que la DLL. Par exemple, si le nom de la DLL est MyLibrary. dll, la valeur de l’attribut Name utilisé dans l' \<élément assemblyIdentity> du manifeste peut également être MyLibrary. Dans certains cas, lorsqu’une bibliothèque a une extension autre que. dll (par exemple, un projet de contrôles ActiveX MFC crée une bibliothèque. ocx), vous pouvez créer un manifeste d’assembly externe. Dans ce cas, le nom de l’assembly et son manifeste doivent être différents du nom de la DLL (par exemple, MyAssembly, MyAssembly. manifest et MyLibrary. ocx). Toutefois, il est toujours recommandé de renommer ces bibliothèques avec l’extension. dll et d’incorporer le manifeste en tant que ressource pour réduire le coût de maintenance futur de cet assembly. Pour plus d’informations sur la recherche d’assemblys privés dans le système d’exploitation, consultez [séquence de recherche](/windows/win32/SbsCs/assembly-searching-sequence)d’assemblys.

Cette modification peut permettre le déploiement des DLL correspondantes en tant qu' [assembly privé](/windows/win32/Msi/private-assemblies) dans un dossier local de l’application ou en tant qu' [assembly partagé](/windows/win32/Msi/shared-assemblies) dans le cache de l’assembly WinSxS. Vous devez suivre plusieurs étapes pour obtenir le comportement d’exécution correct de ce nouvel assembly. elles sont décrites dans [indications pour la création d’assemblys côte à côte](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies). Une fois qu’un assembly est correctement créé, il peut être déployé en tant qu’assembly partagé ou privé avec une application qui en dépend. Lors de l’installation d’assemblys côte à côte en tant qu’assembly partagé, vous pouvez suivre les instructions fournies dans [installation d’assemblys Win32 pour le partage côte à côte sur Windows XP](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp) ou utiliser des [modules de fusion](/windows/win32/msi/merge-modules). Lors de l’installation d’assemblys côte à côte en tant qu’assembly privé, vous pouvez simplement copier la DLL, les ressources et le manifeste de l’assembly correspondants dans le cadre du processus d’installation dans le dossier local de l’application sur l’ordinateur cible, ce qui garantit que cet assembly peut être trouvé par le chargeur lors de l’exécution (voir [séquence de recherche d’assembly](/windows/win32/SbsCs/assembly-searching-sequence)). Une autre méthode consiste à utiliser [Windows Installer](/windows/win32/Msi/windows-installer-portal) et à suivre les instructions fournies dans [installation d’assemblys Win32 pour l’utilisation privée d’une application sur Windows XP](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp).

## <a name="see-also"></a>Voir aussi

[Génération d’applications isolées C/C++](building-c-cpp-isolated-applications.md)<br/>
[Génération d’applications isolées C/C++ et d’assemblys côte à côte](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
