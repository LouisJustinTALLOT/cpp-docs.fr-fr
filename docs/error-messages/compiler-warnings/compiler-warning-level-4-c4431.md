---
title: Avertissement du compilateur (niveau 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: d4d803ef003f2c8367c750cf6d6aef07e4032140
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185358"
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
