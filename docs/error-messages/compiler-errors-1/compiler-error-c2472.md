---
description: 'En savoir plus sur : erreur du compilateur C2472'
title: Erreur du compilateur C2472
ms.date: 11/04/2016
f1_keywords:
- C2472
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
ms.openlocfilehash: a1d4d668c1e7151771a2df85e888384c6c3ea028
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164495"
---
# <a name="compiler-error-c2472"></a>Erreur du compilateur C2472

> '*Function*'ne peut pas être généré dans du code managé : '*message*'; compiler avec/CLR pour générer une image mixte

## <a name="remarks"></a>Notes

Cette erreur se produit quand des types non pris en charge par le code managé sont utilisés dans un environnement CLR pur. Compilez avec **/clr** pour résoudre l’erreur.

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

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

- [/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)
