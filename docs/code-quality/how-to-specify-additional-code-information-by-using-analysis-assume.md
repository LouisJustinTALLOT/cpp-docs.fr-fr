---
title: Utiliser _Analysis_assume pour les indicateurs d’analyse du code
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
ms.openlocfilehash: 00577e6cc5ebd30e38e4fb7204b93c3ecf3fe112
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418738"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Comment : spécifier des informations de code supplémentaires à l’aide de _Analysis_assume

Vous pouvez fournir des indications sur l’outil d’analyse du code pourC++ C/code qui aide le processus d’analyse et réduire les avertissements. Pour fournir des informations supplémentaires, utilisez la fonction suivante :

`_Analysis_assume(`  `expr`  `)`

`expr`-toute expression supposée avoir la valeur true.

L’outil d’analyse du code suppose que la condition représentée par l’expression est vraie au point où la fonction apparaît et reste true jusqu’à ce que l’expression soit modifiée, par exemple, en l’assignant à une variable.

> [!NOTE]
> `_Analysis_assume` n’a pas d’impact sur l’optimisation du code. En dehors de l’outil d’analyse du code, `_Analysis_assume` est défini comme une absence d’opération.

## <a name="example"></a>Exemple

Le code suivant utilise `_Analysis_assume` pour corriger l’avertissement d’analyse du code [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Voir aussi

- [__assume](/cpp/intrinsics/assume)