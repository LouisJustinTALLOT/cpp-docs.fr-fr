---
title: Avertissement du compilateur (niveau 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 1e089c45598a53ff337e389feb2a6983a2997041
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684623"
---
# <a name="compiler-warning-level-1-c4789"></a>Avertissement du compilateur (niveau 1) C4789

> la mémoire tampon'*identificateur*'de taille *N* octets sera saturée ; *M* octets seront écrits en commençant à l’offset *L*

## <a name="remarks"></a>Notes

**C4789** avertit les dépassements de mémoire tampon lors de l’utilisation de fonctions runtime C (CRT) spécifiques. Il peut également signaler des incompatibilités de taille lorsque des paramètres sont passés ou que des affectations sont effectuées. L’avertissement est possible si la taille des données est connue au moment de la compilation. Cet avertissement s'applique aux situations susceptibles d'échapper à la détection standard des non-correspondances de tailles de données.

**C4789** avertit quand des données sont copiées dans un bloc de données qui est trop petit au moment de la compilation.

L’avertissement se produit si la copie utilise la forme intrinsèque de l’une de ces fonctions CRT :

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

L’avertissement s’affiche également lorsque vous effectuez un cast d’un paramètre en un type de données plus grand, puis faites une assignation de copie à partir d’une référence lvalue.

Visual C++ peut générer cet avertissement pour un chemin d’accès de code qui ne s’exécute jamais. Vous pouvez désactiver temporairement l'avertissement à l'aide de `#pragma`, comme illustré dans l'exemple suivant :

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

Cet idiome empêche Visual C++ de générer l’avertissement pour ce bloc de code spécifique. `#pragma warning(push)` conserve l'état existant avant que `#pragma warning(disable: 4789)` le modifie. `#pragma warning(pop)` restaure l'état de type push et supprime les effets de `#pragma warning(disable:4789)`. Pour plus d’informations sur la directive de préprocesseur C++ `#pragma` , consultez directives [Warning](../../preprocessor/warning.md) et [pragma et le mot clé __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="examples"></a>Exemples

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

L'exemple suivant génère également l'erreur C4789.

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

int main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```
