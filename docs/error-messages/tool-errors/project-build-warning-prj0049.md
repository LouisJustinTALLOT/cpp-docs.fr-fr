---
title: Avertissement de génération de projet PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: e857a50215dc7516c0e2ec45a97638c76f40f43b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191745"
---
# <a name="project-build-warning-prj0049"></a>Avertissement de génération de projet PRJ0049

La cible référencée «\<référence > » requiert .NET Framework \<MinFrameworkVersion > et ne pourra pas s’exécuter sur le Framework cible de ce projet

Les applications créées à l’aide de Visual Studio 2008 peuvent spécifier la version du .NET Framework qu’elles doivent cibler. Si vous ajoutez une référence à un assembly ou un projet qui dépend d’une version de la .NET Framework qui est ultérieure à la version ciblée, vous obtiendrez cet avertissement au moment de la compilation.

### <a name="to-correct-this-warning"></a>Pour corriger cet avertissement

1. Choisissez l’un des éléments suivants :

   - Modifiez l’infrastructure ciblée dans la boîte de dialogue **pages de propriétés** du projet afin qu’elle soit ultérieure ou égale à la version minimale du .NET Framework de tous les assemblys et projets référencés. Pour plus d’informations, consultez [Ajout de références](../../build/adding-references-in-visual-cpp-projects.md).

   - Supprimez la référence à l’assembly ou au projet dont la version de Framework minimale est ultérieure à celle de l’infrastructure ciblée. Ces éléments sont signalés par une icône d’avertissement dans les **pages de propriétés**du projet.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements de génération de projet (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
