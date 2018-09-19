---
title: Compilateur avertissement (niveau 1) C4789 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4789
dev_langs:
- C++
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 167bca2a4596a738813309eceb7e22751b5584b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087329"
---
# <a name="compiler-warning-level-1-c4789"></a>Avertissement du compilateur (niveau 1) C4789

> mémoire tampon '*identificateur*» de taille *N* octets seront dépassées ; *M* octets seront écrits en commençant au décalage *L*

## <a name="remarks"></a>Notes

Signale tout dépassement de mémoire tampon lors de l'utilisation de fonctions CRT (Runtime C) spécifiques, quand des paramètres sont passés et des affectations effectuées, de façon à ce que les tailles des données soient connues au moment de la compilation. Cet avertissement s'applique aux situations susceptibles d'échapper à la détection standard des non-correspondances de tailles de données.

L'avertissement s'affiche quand les données, dont la longueur est connue au moment de la compilation, sont copiées et placées dans un bloc de données dont la taille est identifiée au moment de la compilation comme étant trop petite pour les données. La copie doit être effectuée à l'aide de la forme intrinsèque de l'une des fonctions CRT suivantes :

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

L'avertissement apparaît également quand le type de données d'un paramètre est incompatible avec un cast et qu'une tentative d'assignation de copie d'une référence lvalue est effectuée ultérieurement.

Visual C++ peut générer cet avertissement pour un chemin d'accès de code qui ne s'exécute jamais. Vous pouvez désactiver temporairement l'avertissement à l'aide de `#pragma`, comme illustré dans l'exemple suivant :

```cpp
#pragma(push)
#pragma warning ( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma(pop)
```

Cela empêche Visual C++ de générer l'avertissement pour ce bloc de code spécifique. `#pragma(push)` conserve l'état existant avant que `#pragma warning(disable: 4789)` le modifie. `#pragma(pop)` restaure l'état de type push et supprime les effets de `#pragma warning(disable:4789)`. Pour plus d’informations sur la directive de préprocesseur C++ `#pragma`, consultez [avertissement](../../preprocessor/warning.md) et [Directives Pragma et mot clé _pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C4789.

```cpp
// C4789.cpp
// compile with: /Oi /W1 /c
#include <string.h>
#include <stdio.h>

int main()
{
    char a[20];
    strcpy(a, "0000000000000000000000000\n");   // C4789

    char buf2[20];
    memset(buf2, 'a', 21);   // C4789

    char c;
    wchar_t w = 0;
    memcpy(&c, &w, sizeof(wchar_t));
}
```

## <a name="example"></a>Exemple

L'exemple suivant génère également l'erreur C4789.

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

void main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```