---
title: Avertissement du compilateur (niveau 4) C4337
ms.date: 11/04/2016
f1_keywords:
- C4337
helpviewer_keywords:
- C4337
ms.assetid: 70bc72d9-aac5-45cd-abd3-ebe42a05897b
ms.openlocfilehash: f86d03e30e2776a8dae4cf56032c45d0022ca01d
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683309"
---
# <a name="compiler-warning-level-4-c4337"></a>Avertissement du compilateur (niveau 4) C4337

la bibliothèque de types à références croisées’typelib1 'dans’typelib2 'est automatiquement importée

L’attribut auto_search de [la directive #import](../../preprocessor/hash-import-directive-cpp.md) a provoqué l’importation implicite d’une bibliothèque de types.

Deux bibliothèques de types sont fournies sur le disque créé à partir des deux fichiers suivants (compilés avec MIDL. exe) :

```
// C4337a.idl
[
  uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12B)
]
library C4337aLib
{
   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12C)]
   enum E_C4337a
   {
      one = 0,
      two = 1,
      three = 2
    };
};
```

puis le deuxième fichier. idl,

```
// C4337b.idl
[
   uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12D)
]

library C4337bLib
{
   importlib("c4337a.tlb");

   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12E)]
   struct S_C4337b
   {
      enum E_C4337a e;
   };
};
```

L’exemple suivant génère l’C4337 :

```cpp
// C4337.cpp
// compile with: /W4 /LD
#import "c4337b.tlb" auto_search   // C4337
// explicitly #import all type libraries to resolve
// #import "C4337a.tlb"
// #import "C4337b.tlb"
```