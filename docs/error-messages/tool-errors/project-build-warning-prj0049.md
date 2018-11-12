---
title: Avertissement de génération de projet PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: a451b7fe7b2f7cd89f8898232badf0d3b7e9f138
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447214"
---
# <a name="project-build-warning-prj0049"></a>Avertissement de génération de projet PRJ0049

Cible référencé '\<référence >' requiert .NET Framework \<MinFrameworkVersion > et ne sont pas exécutés sur le framework cible de ce projet

Les applications créées à l’aide de Visual Studio 2008 peuvent spécifier quelle version du .NET Framework, elles doivent cibler. Si vous ajoutez une référence à un assembly ou un projet qui dépend d’une version du .NET Framework ultérieure à la version ciblée, vous obtiendrez cet avertissement au moment de la compilation.

### <a name="to-correct-this-warning"></a>Pour corriger cet avertissement

1. Choisissez l'une des valeurs suivantes :

   - Modifier le framework ciblé dans le projet **Pages de propriétés** afin qu’il soit postérieure ou égale à la version de framework minimale de tous les assemblys référencés et projets de boîte de dialogue. Pour plus d’informations, consultez [l’ajout de références](../../ide/adding-references-in-visual-cpp-projects.md).

   - Supprimez la référence à l’assembly ou le projet qui a une version de framework minimale qui est ultérieure au framework ciblé. Ces éléments sont marqués avec une icône d’avertissement dans le projet **Pages de propriétés**.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements de génération de projet (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)