---
title: Avertissement de génération PRJ0049 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 169ba63318f630ac6a63b18d34fd6a7d829f4f90
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110885"
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