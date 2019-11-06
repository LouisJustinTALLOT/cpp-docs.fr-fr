---
title: Portage de bibliothèques tierces
ms.date: 10/29/2019
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: 89460af1ad0b356f4f5952141636a9f067131750
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627187"
---
# <a name="porting-third-party-libraries"></a>Portage de bibliothèques tierces

Quand vous mettez à niveau un projet de Visual Studio 2013 ou version antérieure vers la version C++actuelle de Visual, vous devez également mettre à niveau toutes les bibliothèques que le projet utilise, afin que la bibliothèque et votre projet soient générés avec la même version et la même version du compilateur. Si vous n’avez pas accès au code source de la bibliothèque et que la bibliothèque n’est pas disponible par le biais de vcpkg, vous devez obtenir un fichier binaire mis à jour auprès du fournisseur de la bibliothèque. (Pour plus d’informations, consultez [Vue d’ensemble des problèmes de mise à niveau potentiels](overview-of-potential-upgrade-issues-visual-cpp.md)).

Lors de la mise à niveau d’une application de Visual Studio 2015 ou Visual Studio 2017 vers Visual Studio 2019, il n’est pas nécessaire de mettre à niveau les dépendances, car le code généré par ces trois versions est compatible binaire. Pour plus d’informations, consultez [ C++ compatibilité binaire entre Visual Studio 2015 et Visual Studio 2019](binary-compat-2015-2017.md).

## <a name="vcpkg-for-open-source-libraries"></a>vcpkg pour les bibliothèques Open source

Dans le passé, la recherche et la mise à niveau de bibliothèques tierces représentaient parfois une tâche loin d’être futile. Pour faciliter l’acquisition et la régénération C++ de bibliothèques Open source tierces, l’équipe C++ visuelle a créé un outil en ligne de commande appelé **outil d’empaquetage VC + +** ou **vcpkg**. Vcpkg comporte un catalogue de nombreuses bibliothèques open source C++ populaires dans lequel vous pouvez effectuer des recherches. Vous pouvez installer n’importe quelle bibliothèque dans le catalogue directement à partir de la ligne de commande vcpkg. Quand vous installez une bibliothèque, Vcpkg crée une arborescence de répertoires sur votre ordinateur et ajoute les fichiers .h, .lib et binaires à ce dossier. Vous pouvez utiliser ce dossier dans votre ligne de commande de compilation, ou l’intégrer à Visual Studio 2015 ou version ultérieure à l’aide de la commande vcpkg integrate install. Après avoir intégré un emplacement de bibliothèque, Visual Studio peut le trouver et l’ajouter à n’importe quel projet que vous créez. Pour employer une bibliothèque, utilisez simplement `#include`. Visual Studio ajoute automatiquement le chemin du fichier .lib aux paramètres du projet, puis copie la dll dans votre dossier solution. Pour plus d’informations, consultez [vcpkg : Gestionnaire de package pour C++](../build/vcpkg.md).

## <a name="reporting-issues"></a>Problèmes liés aux rapports

Si votre bibliothèque open source n’est pas présente dans **vcpkg** Catalog, vous pouvez ouvrir un problème sur le [référentiel GitHub](https://github.com/Microsoft/vcpkg/issues) , où la communauté et l' C++ équipe visuelle peuvent la voir et créer éventuellement le fichier de port pour cette bibliothèque.

## <a name="see-also"></a>Voir aussi

[Guide du portage et de la mise à niveau de Visual C++](visual-cpp-porting-and-upgrading-guide.md)
