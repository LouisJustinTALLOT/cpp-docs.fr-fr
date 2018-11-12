---
title: Général, page de propriétés (Fichier)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 224a205bb87b89f073676275d67e3cdd127b79af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655249"
---
# <a name="general-property-page-file"></a>Général, page de propriétés (Fichier)

Quand un fichier est sélectionné dans **l’Explorateur de solutions**, la page de propriétés **Général** sous le nœud **Propriétés de configuration** contient les propriétés suivantes :

- **Exclure de la génération**

   Spécifie si le fichier doit se trouver dans la génération de la configuration actuelle.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

- **Outil**

   Outil qui doit être utilisé pour générer ce fichier. Pour plus d’informations, consultez [Spécification des outils de génération personnalisée](../ide/specifying-custom-build-tools.md).

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Pour plus d’informations sur l’accès à la page de propriétés **Général** sous le nœud **Propriétés de configuration**, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).

Pour les projets non-Windows, consultez [Informations de référence sur les pages de propriétés dans un projet Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../ide/property-pages-visual-cpp.md)