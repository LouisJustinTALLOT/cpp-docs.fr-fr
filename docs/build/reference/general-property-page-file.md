---
title: Général, page de propriétés (Fichier)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 66e26cabf5af85091000e6cda144898789c581df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292223"
---
# <a name="general-property-page-file"></a>Général, page de propriétés (Fichier)

Quand un fichier est sélectionné dans **l’Explorateur de solutions**, la page de propriétés **Général** sous le nœud **Propriétés de configuration** contient les propriétés suivantes :

- **Exclure de la génération**

   Spécifie si le fichier doit se trouver dans la génération de la configuration actuelle.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

- **Outil**

   Outil qui doit être utilisé pour générer ce fichier. Pour plus d’informations, consultez [Spécification des outils de génération personnalisée](../specifying-custom-build-tools.md).

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Pour plus d’informations sur la façon d’accéder à la **général** page de propriétés sous la **propriétés de Configuration** nœud, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

Pour les projets non Windows, consultez [référence de Page de propriété Linux C++](../../linux/prop-pages-linux.md).

## <a name="see-also"></a>Voir aussi

[Référence de page de propriété de projet C++](property-pages-visual-cpp.md)