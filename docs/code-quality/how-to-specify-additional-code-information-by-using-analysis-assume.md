---
description: En savoir plus sur la façon de spécifier des informations de code supplémentaires à l’aide de _Analysis_assume_.
title: Utiliser _Analysis_assume_ pour les indicateurs d’analyse du code
ms.date: 12/16/2020
ms.topic: conceptual
f1_keywords:
- _Analysis_assume_
helpviewer_keywords:
- _Analysis_assume_
ms.openlocfilehash: f4244a896d4334cb6c5e857e63b39be0cd53b08b
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645122"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume_"></a>Comment spécifier des informations de code supplémentaires à l’aide de `_Analysis_assume_`

Vous pouvez fournir des indications à l’outil d’analyse du code pour le code C/C++ qui aide le processus d’analyse et à réduire les avertissements. Pour fournir des informations supplémentaires, utilisez la macro de fonction suivante :

`_Analysis_assume( expr )`

*`expr`* -toute expression supposée avoir la valeur true.

L’outil d’analyse du code suppose que la condition représentée par l’expression *`expr`* est vraie au point où la fonction apparaît. De plus, il reste vrai jusqu’à ce que *`expr`* soit modifié, par exemple, en l’assignant à une variable.

> [!NOTE]
> `_Analysis_assume_` n’a pas d’impact sur l’optimisation du code. En dehors de l’outil d’analyse du code, `_Analysis_assume_` est défini comme une absence d’opération.

## <a name="example"></a>Exemple

Le code suivant utilise `_Analysis_assume_` pour corriger l’avertissement d’analyse du code [C6388](../code-quality/c6388.md):

```cpp
#include <windows.h>
#include <codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume_(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Voir aussi

- [__assume](../intrinsics/assume.md)
