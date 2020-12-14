---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2028'
title: Erreur des outils Éditeur de liens LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: 31b20cc572a44b1260f58eb03519b60050c0246c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275722"
---
# <a name="linker-tools-error-lnk2028"></a>Erreur des outils Éditeur de liens LNK2028

«*exported_function*» (*Decorated_Name*) référencé dans la fonction «*function_containing_function_call*» (*Decorated_Name*)

## <a name="remarks"></a>Notes

Lorsque vous tentez d’importer une fonction native dans une image pure, n’oubliez pas que les conventions d’appel implicites diffèrent entre les compilations native et pure.

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

## <a name="examples"></a>Exemples

Cet exemple de code génère un composant avec une fonction exportée, native, dont la Convention d’appel est implicitement [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

L’exemple suivant crée un client pur qui utilise la fonction native. Toutefois, la Convention d’appel sous **/clr : pure** est [__clrcall](../../cpp/clrcall.md). L’exemple suivant génère l’LNK2028.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
