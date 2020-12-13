---
description: 'En savoir plus sur : pragma Pack'
title: pack, pragma
ms.date: 07/22/2020
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: d4e4cbba13efabd148fdd61f59eebb15c56b1c41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333196"
---
# <a name="pack-pragma"></a>pack, pragma

Spécifie l’alignement de la compression pour les membres de la structure, de l’Union et de la classe.

## <a name="syntax"></a>Syntaxe

> **`#pragma pack( show )`**\
> **`#pragma pack( push`** [ **`,`** *`identifier`* ] [ **`,`** *`n`* ] **`)`**\
> **`#pragma pack( pop`** [ **`,`** { *`identifier`* | *`n`* } ] **`)`**\
> **`#pragma pack(`** [ *`n`* ] **`)`**

### <a name="parameters"></a>Paramètres

**`show`**\
Facultatif Affiche la valeur d’octet actuelle pour l’alignement de compression. La valeur est affichée par un message d'avertissement.

**`push`**\
Facultatif Exécute un push de la valeur d’alignement de compression actuelle sur la pile interne du compilateur et définit la valeur d’alignement de la compression actuelle sur *n*. Si *n* n’est pas spécifié, la valeur actuelle de l’alignement de compression fait l’objet d’un push.

**`pop`**\
Facultatif Supprime l’enregistrement du haut de la pile interne du compilateur. Si *n* n’est pas spécifié avec **`pop`** , la valeur de compression associée à l’enregistrement obtenu en haut de la pile est la nouvelle valeur d’alignement de la compression. Si *n* est spécifié, par exemple, `#pragma pack(pop, 16)` *n* devient la nouvelle valeur d’alignement de la compression. Si vous utilisez une liste déroulante, *`identifier`* par exemple,, `#pragma pack(pop, r1)` tous les enregistrements de la pile sont dépilés jusqu’à ce que l’enregistrement *`identifier`* trouvé soit trouvé. Cet enregistrement est dépilé et la valeur de compression associée à l’enregistrement trouvé en haut de la pile devient la nouvelle valeur d’alignement de la compression. Si vous utilisez un pop *`identifier`* qui n’est trouvé dans aucun enregistrement sur la pile, **`pop`** est ignoré.

L’instruction `#pragma pack (pop, r1, 2)` est équivalente à `#pragma pack (pop, r1)` suivie de `#pragma pack(2)` .

*`identifier`*\
Facultatif En cas d’utilisation avec **`push`** , assigne un nom à l’enregistrement sur la pile interne du compilateur. En cas d’utilisation avec **`pop`** , dépile les enregistrements de la pile interne jusqu’à ce que *`identifier`* soit supprimé. Si est *`identifier`* introuvable sur la pile interne, rien n’est dépilé.

*`n`*\
Facultatif Spécifie la valeur, en octets, à utiliser pour la compression. Si l’option de compilateur [`/Zp`](../build/reference/zp-struct-member-alignment.md) n’est pas définie pour le module, la valeur par défaut de *`n`* est 8. Les valeurs valides sont 1, 2, 4, 8 et 16. L’alignement d’un membre se trouve sur une limite qui est un multiple de *`n`* , ou un multiple de la taille du membre, la valeur la plus petite étant retenue.

## <a name="remarks"></a>Notes

Pour *empaqueter* une classe, vous pouvez placer ses membres directement après les autres en mémoire. Cela peut signifier que certains ou tous les membres peuvent être alignés sur une limite inférieure à l’alignement par défaut de l’architecture cible. **`pack`** donne le contrôle au niveau de la déclaration de données. Il diffère de l’option du compilateur [`/Zp`](../build/reference/zp-struct-member-alignment.md) , qui fournit uniquement le contrôle au niveau du module. **Pack** prend effet à la première **`struct`** **`union`** déclaration, ou **`class`** après que le pragma a été affiché. **`pack`** n’a aucun effet sur les définitions. L’appel de **`pack`** avec aucun argument n’affecte *`n`* à la valeur définie dans l’option du compilateur **`/Zp`** . Si l’option de compilateur n’est pas définie, la valeur par défaut est 8 pour x86, ARM et ARM64. La valeur par défaut est 16 pour x64 natif.

Si vous modifiez l’alignement d’une structure, elle ne peut pas utiliser autant d’espace en mémoire. Toutefois, vous pouvez constater une perte de performances ou même obtenir une exception générée par le matériel pour un accès non aligné. Vous pouvez modifier ce comportement d’exception à l’aide de [`SetErrorMode`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) .

Pour plus d’informations sur la modification de l’alignement, consultez les articles suivants :

- [`alignof`](../cpp/alignof-operator.md)

- [`align`](../cpp/align-cpp.md)

- [`__unaligned`](../cpp/unaligned.md)

- [Exemples d’alignement de structure](../build/x64-software-conventions.md#examples-of-structure-alignment) (spécifique à x64)

   > [!WARNING]
   > Dans Visual Studio 2015 et versions ultérieures, vous pouvez utiliser les **`alignas`** opérateurs standard et **`alignof`** , qui, contrairement à **`__alignof`** et, **`__declspec( align )`** sont portables entre les compilateurs. La norme C++ ne traite pas la compression. vous devez donc toujours utiliser **`pack`** (ou l’extension correspondante sur d’autres compilateurs) pour spécifier des alignements plus petits que la taille de mot de l’architecture cible.

## <a name="examples"></a>Exemples

L’exemple suivant montre comment utiliser le **`pack`** pragma pour modifier l’alignement d’une structure.

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

L’exemple suivant montre comment utiliser la syntaxe *Push*, *pop* et *Show* .

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810

// pop to the identifier and then set
// the value of the current packing alignment:
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et `__pragma` mot clé](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
