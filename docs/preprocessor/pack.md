---
title: pack
ms.date: 12/17/2018
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: da4484ec86d39c8fa55a741eadd53a1d614b20dc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510177"
---
# <a name="pack"></a>pack
Spécifie l'alignement de compression pour des membres de structure, d'union et de classe.

## <a name="syntax"></a>Syntaxe

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>Paramètres

**show**<br/>
Facultatif Affiche la valeur d’octet actuelle pour l’alignement de compression. La valeur est affichée par un message d'avertissement.

**push**<br/>
Facultatif Exécute un push de la valeur d’alignement de compression actuelle sur la pile interne du compilateur et définit la valeur d’alignement de la compression actuelle sur *n*. Si *n* n’est pas spécifié, la valeur actuelle de l’alignement de compression fait l’objet d’un push.

**pop**<br/>
Facultatif Supprime l’enregistrement du haut de la pile interne du compilateur. Si *n* n’est pas spécifié avec **pop**, la valeur de compression associée à l’enregistrement obtenu en haut de la pile est la nouvelle valeur d’alignement de compression. Si *n* est spécifié, par exemple `#pragma pack(pop, 16)`, *n* devient la nouvelle valeur d’alignement de la compression. Si vous effectuez un pop avec l' *identificateur*(par `#pragma pack(pop, r1)`exemple,), tous les enregistrements de la pile sont dépilés jusqu’à ce que l’enregistrement ayant l' *identificateur* soit trouvé. Cet enregistrement est dépilé et la valeur de compression associée à l'enregistrement obtenu en haut de la pile est la nouvelle valeur d'alignement de compression. Si vous pop avec un *identificateur* qui n’est trouvé dans aucun enregistrement sur la pile, le **pop** est ignoré.

*identifier*<br/>
Facultatif En cas d’utilisation avec *Push*, assigne un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’il est utilisé avec **pop**, dépile les enregistrements de la pile interne jusqu’à la suppression de l' *identificateur* ; Si l' *identificateur* est introuvable sur la pile interne, rien n’est dépilé.

*n*<br/>
Facultatif Spécifie la valeur, en octets, à utiliser pour la compression. Si l’option de compilateur [/ZP](../build/reference/zp-struct-member-alignment.md) n’est pas définie pour le module, la valeur par défaut de *n* est 8. Les valeurs valides sont 1, 2, 4, 8 et 16. L’alignement d’un membre se fera sur une limite qui est un multiple de *n* ou un multiple de la taille du membre, la valeur la plus petite étant retenue.

`#pragma pack(pop, identifier, n)`n’est pas défini.

## <a name="remarks"></a>Notes

La compression d'une classe consiste à placer ses membres directement les uns après les autres dans la mémoire, ce qui peut signifier que certains ou l'ensemble des membres peuvent être alignés sur une limite inférieure à l'alignement par défaut de l'architecture cible. **Pack** donne le contrôle au niveau de la déclaration de données. Cela diffère de l’option de compilateur [/ZP](../build/reference/zp-struct-member-alignment.md), qui fournit uniquement le contrôle au niveau du module. **Pack** prend effet au niveau de la première déclaration de **struct**, d' **Union**ou de **classe** une fois que le pragma est visible. **Pack** n’a aucun effet sur les définitions. L’appel de **Pack** sans arguments affecte la valeur *n* à la valeur définie dans `/Zp`l’option du compilateur. Si l'option du compilateur n'est pas définie, la valeur par défaut est 8.

Si vous modifiez l'alignement d'une structure, il est possible qu'elle n'utilise pas autant d'espace en mémoire, mais vous risquez de constater une baisse des performances ou même d'obtenir une exception générée par le matériel relative au non-alignement de l'accès.  Vous pouvez modifier ce comportement d’exception à l’aide de [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode).

Pour plus d'informations sur la façon de modifier l'alignement, consultez les rubriques suivantes :

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Exemples d’alignement de structure](../build/x64-software-conventions.md#examples-of-structure-alignment) (spécifique à x64)

   > [!WARNING]
   > Notez que, dans Visual Studio 2015 et versions ultérieures, vous pouvez utiliser les opérateurs alignas et alignof standard qui sont portables entre les compilateurs, contrairement à `__alignof` et `declspec( align )`. La C++ norme ne traite pas la compression. vous devez donc toujours utiliser **Pack** (ou l’extension correspondante sur d’autres compilateurs) pour spécifier des alignements plus petits que la taille de mot de l’architecture cible.

## <a name="examples"></a>Exemples

L’exemple suivant montre comment utiliser le pragma **Pack** pour modifier l’alignement d’une structure.

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

L’exemple suivant montre comment utiliser la syntaxe *Push*, *pop*et *Show* .

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)