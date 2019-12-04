---
title: Erreur du compilateur C3510
ms.date: 11/04/2016
f1_keywords:
- C3510
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
ms.openlocfilehash: 3f9dea77b739aa59474e60cf852fff2577ab6ba9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753625"
---
# <a name="compiler-error-c3510"></a>Erreur du compilateur C3510

Impossible de trouver la bibliothèque de types dépendante’type_lib'

[no_registry](../../preprocessor/no-registry.md) et [auto_search](../../preprocessor/auto-search.md) ont été passés à `#import` mais le compilateur n’a pas pu trouver une bibliothèque de types référencée.

Pour résoudre cette erreur, assurez-vous que toutes les bibliothèques de types et les bibliothèques de types référencées sont disponibles pour le compilateur.

L’exemple suivant génère l’C3510 :

Supposons que les deux bibliothèques de types suivantes ont été générées et que C3510a. tlb a été supprimé ou non sur le chemin d’accès.

```
// C3510a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C3510aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C3510
   {
      one, two, three
   };
};
```

Puis le code source de la deuxième bibliothèque de types :

```
// C3510b.idl
// post-build command: del /f C3510a.tlb
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
library C3510bLib
{
   importlib ("C3510a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
   struct S_C3510 {
      enum E_C3510 e;
   };
};
```

Puis le code client :

```cpp
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```
