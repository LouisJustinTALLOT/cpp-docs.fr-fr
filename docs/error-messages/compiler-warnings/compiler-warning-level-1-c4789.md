---
title: Avertissement du compilateur (niveau 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36a5032098c5caabb1b050833e487fd58679a782
ms.sourcegitcommit: 6e4dd21759caaed262a7255735cf8d6e8fb9f4d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476850"
---
# <a name="compiler-warning-level-1-c4789"></a>Avertissement du compilateur (niveau 1) C4789

> mémoire tampon '*identificateur*» de taille *N* octets seront dépassées ; *M* octets seront écrits en commençant au décalage *L*

## <a name="remarks"></a>Notes

**Erreur C4789** signale les dépassements de mémoire tampon lorsque des fonctions C Runtime (CRT) spécifiques sont utilisées. Il peut également signaler les incompatibilités de taille lorsque les paramètres sont transmis ou affectations effectuées. L’avertissement est possible si les tailles des données sont connues au moment de la compilation. Cet avertissement s'applique aux situations susceptibles d'échapper à la détection standard des non-correspondances de tailles de données.

**Erreur C4789** vous avertit quand données sont copiées dans un bloc de données qui est connu comme étant trop petite à la compilation.

L’avertissement se produit si la copie utilise la forme intrinsèque d’une de ces fonctions CRT :

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

L’avertissement s’affiche également lorsque vous effectuez un cast d’un paramètre à un type de données plus grand et effectuez une assignation de copie à partir d’une référence lvalue.

Visual C++ peut générer cet avertissement pour un chemin d’accès du code qui s’exécute jamais. Vous pouvez désactiver temporairement l'avertissement à l'aide de `#pragma`, comme illustré dans l'exemple suivant :

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

Cet idiome empêche Visual C++ de générer l’avertissement pour ce bloc de code spécifique. `#pragma warning(push)` conserve l'état existant avant que `#pragma warning(disable: 4789)` le modifie. `#pragma warning(pop)` restaure l'état de type push et supprime les effets de `#pragma warning(disable:4789)`. Pour plus d’informations sur la directive de préprocesseur C++ `#pragma`, consultez [avertissement](../../preprocessor/warning.md) et [Directives Pragma et mot clé _pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

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