---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4336'
title: Avertissement du compilateur (niveau 4) C4336
ms.date: 11/04/2016
f1_keywords:
- C4336
helpviewer_keywords:
- C4336
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
ms.openlocfilehash: d41ca5584864327b3012e79af97f2857e3f93d42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257717"
---
# <a name="compiler-warning-level-4-c4336"></a>Avertissement du compilateur (niveau 4) C4336

importer la bibliothèque de types à références croisées’type_lib1 'avant d’importer’type_lib2 '

Une bibliothèque de types a été référencée avec la directive [#import](../../preprocessor/hash-import-directive-cpp.md) . Toutefois, la bibliothèque de types contenait une référence à une autre bibliothèque de types qui n’a pas été référencée avec `#import` . Ce fichier. tlb a été trouvé par le compilateur.

Deux bibliothèques de types sont fournies sur le disque créé à partir des deux fichiers suivants (compilés avec midl.exe) :

```
// c4336a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library c4336aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C4336
   {
      one, two, three
   };
};
```

La deuxième bibliothèque de types :

```
// c4336b.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4336bLib
{
   importlib ("c4336a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4336
   {
      enum E_C4336 e;
   };
};
```

L’exemple suivant génère l’C4336 :

```cpp
// C4336.cpp
// compile with: /W4 /LD
// #import "C4336a.tlb"
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve
```
