---
description: 'En savoir plus sur : avertissement de génération de projet projet PRJ0049'
title: Avertissement de génération de projet PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: 423b2220cdc80408c71f96c65eb078763291ec3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206355"
---
# <a name="project-build-warning-prj0049"></a>Avertissement de génération de projet PRJ0049

La cible référencée' \<Reference> 'requiert .NET Framework \<MinFrameworkVersion> et ne pourra pas s’exécuter sur le Framework cible de ce projet

Les applications créées à l’aide de Visual Studio 2008 peuvent spécifier la version du .NET Framework qu’elles doivent cibler. Si vous ajoutez une référence à un assembly ou un projet qui dépend d’une version de la .NET Framework qui est ultérieure à la version ciblée, vous obtiendrez cet avertissement au moment de la compilation.

### <a name="to-correct-this-warning"></a>Pour corriger cet avertissement

1. Choisissez l’un des éléments suivants :

   - Modifiez l’infrastructure ciblée dans la boîte de dialogue **pages de propriétés** du projet afin qu’elle soit ultérieure ou égale à la version minimale du .NET Framework de tous les assemblys et projets référencés. Pour plus d’informations, consultez [Ajout de références](../../build/adding-references-in-visual-cpp-projects.md).

   - Supprimez la référence à l’assembly ou au projet dont la version de Framework minimale est ultérieure à celle de l’infrastructure ciblée. Ces éléments sont signalés par une icône d’avertissement dans les **pages de propriétés** du projet.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements de génération de projet (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
