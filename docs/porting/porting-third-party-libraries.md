---
title: "Portage de bibliothèques tierces | Microsoft Docs"
ms.custom: 
ms.date: 01/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
caps.latest.revision: "0"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cdcfd815f520ff5d9e3931945eeb7b3597ec2393
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="porting-third-party-libraries"></a>Portage de bibliothèques tierces

Quand vous mettez à niveau un projet vers la version actuelle de Visual C++, vous devez également mettre à niveau toutes les bibliothèques qu’il utilise, afin que la bibliothèque et votre projet soient générés avec les mêmes version et configuration du compilateur. (Pour plus d’informations, consultez [Vue d’ensemble des problèmes de mise à niveau potentiels](overview-of-potential-upgrade-issues-visual-cpp.md)). 

## <a name="introducing-vcpkg"></a>Présentation de vcpkg
Dans le passé, la recherche et la mise à niveau de bibliothèques tierces représentaient parfois une tâche loin d’être futile. Pour faciliter l’acquisition et la régénération de bibliothèques open source tierces C++, l’équipe Visual C++ a créé un outil en ligne de commande appelé l’**outil d’empaquetage VC++** ou **vcpkg**. Vcpkg comporte un catalogue de nombreuses bibliothèques open source C++ populaires dans lequel vous pouvez effectuer des recherches. Vous pouvez installer n’importe quelle bibliothèque dans le catalogue directement à partir de la ligne de commande vcpkg. Quand vous installez une bibliothèque, Vcpkg crée une arborescence de répertoires sur votre ordinateur et ajoute les fichiers .h, .lib et binaires à ce dossier. Vous pouvez utiliser ce dossier dans votre ligne de commande de compilation, ou l’intégrer à Visual Studio 2015 ou version ultérieure à l’aide de la commande vcpkg integrate install. Après avoir intégré un emplacement de bibliothèque, Visual Studio peut le trouver et l’ajouter à n’importe quel projet que vous créez. Pour employer une bibliothèque, utilisez #include, et Visual Studio ajoute automatiquement le chemin d’accès au fichier .lib dans les paramètres du projet et copie la dll dans votre dossier de solution. Pour plus d’informations, consultez [vcpkg : Gestionnaire de package pour C++](../vcpkg.md).


## <a name="reporting-issues"></a>Problèmes liés aux rapports
Si votre bibliothèque ne figure pas dans le catalogue vcpkg, vous pouvez signaler un problème sur le [dépôt GitHub](https://github.com/Microsoft/vcpkg/issues) où la communauté et l’équipe Visual C++ peuvent le voir et éventuellement créer le fichier de port pour cette bibliothèque.

Pour les bibliothèques tierces propriétaires (non-open source), nous vous conseillons de contacter le fournisseur de la bibliothèque. Toutefois, nous aimerions connaître les bibliothèques propriétaires que vous utilisez et qui vous bloquent. Indiquez-nous celle dont vous dépendez (vous pouvez nous contacter à l’adresse vcupgrade@microsoft.com).

  
## <a name="see-also"></a>Voir aussi  
 [Guide du portage et de la mise à niveau de Visual C++](visual-cpp-porting-and-upgrading-guide.md)
