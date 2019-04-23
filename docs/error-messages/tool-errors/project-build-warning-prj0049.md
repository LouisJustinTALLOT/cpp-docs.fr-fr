---
title: Avertissement de génération de projet PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: 0252103757df1c5dc95c9691c6da1d3630d29772
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035557"
---
# <a name="project-build-warning-prj0049"></a>Avertissement de génération de projet PRJ0049

Cible référencé '\<référence >' requiert .NET Framework \<MinFrameworkVersion > et ne sont pas exécutés sur le framework cible de ce projet

Les applications créées à l’aide de Visual Studio 2008 peuvent spécifier quelle version du .NET Framework, elles doivent cibler. Si vous ajoutez une référence à un assembly ou un projet qui dépend d’une version du .NET Framework ultérieure à la version ciblée, vous obtiendrez cet avertissement au moment de la compilation.

### <a name="to-correct-this-warning"></a>Pour corriger cet avertissement

1. Choisissez l'une des valeurs suivantes :

   - Modifier le framework ciblé dans le projet **Pages de propriétés** afin qu’il soit postérieure ou égale à la version de framework minimale de tous les assemblys référencés et projets de boîte de dialogue. Pour plus d’informations, consultez [l’ajout de références](../../build/adding-references-in-visual-cpp-projects.md).

   - Supprimez la référence à l’assembly ou le projet qui a une version de framework minimale qui est ultérieure au framework ciblé. Ces éléments sont marqués avec une icône d’avertissement dans le projet **Pages de propriétés**.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements de génération de projet (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)