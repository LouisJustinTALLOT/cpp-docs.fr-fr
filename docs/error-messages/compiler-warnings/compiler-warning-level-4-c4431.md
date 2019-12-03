---
title: Avertissement du compilateur (niveau 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 102e9bdb2804988875d8c535eb8c266bd8fb03df
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683070"
---
# <a name="compiler-warning-level-4-c4431"></a>Avertissement du compilateur (niveau 4) C4431

spécificateur de type manquant - int est pris en compte par défaut. Remarque : C ne prend plus en charge int par défaut

Cette erreur peut être générée en raison du travail de conformité du compilateur effectué pour Visual Studio 2005 : Visual C++ ne crée plus d’identificateurs non typés comme int par défaut. Le type d’un identificateur doit être spécifié explicitement.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4431.

```c
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```