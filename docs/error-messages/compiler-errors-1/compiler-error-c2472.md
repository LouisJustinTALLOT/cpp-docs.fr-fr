---
title: Erreur du compilateur C2472
ms.date: 11/04/2016
f1_keywords:
- C2472
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
ms.openlocfilehash: d2f104bb61915f8d19d5fff22eea17929c0e8d74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350908"
---
# <a name="compiler-error-c2472"></a>Erreur du compilateur C2472

> «*fonction*' ne peut pas être généré dans le code managé : '*message*' ; compilez avec /clr pour générer une image mixte

## <a name="remarks"></a>Notes

Cette erreur se produit quand des types non pris en charge par le code managé sont utilisés dans un environnement CLR pur. Compilez avec **/clr** pour résoudre l’erreur.

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2472 :

```cpp
// C2472.cpp
// compile with: /clr:pure
// C2472 expected

#include <cstdlib>

int main()
{
   int * __ptr32 p32;
   int * __ptr64 p64;

   p32 = (int * __ptr32)malloc(4);
   p64 = p32;
}
```

## <a name="see-also"></a>Voir aussi

- [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)
