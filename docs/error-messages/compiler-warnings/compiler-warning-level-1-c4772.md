---
title: Avertissement du compilateur (niveau 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 95243ab66d5d0296e1c316ff8dde7add75a030cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540021"
---
# <a name="compiler-warning-level-1-c4772"></a>Avertissement du compilateur (niveau 1) C4772

> \#importation référencé d’un type à partir d’une bibliothèque de types manquante ; «*type manquant*' utilisé comme espace réservé

Une bibliothèque de types a été référencée avec la [#import](../../preprocessor/hash-import-directive-cpp.md) directive. Toutefois, la bibliothèque de types contenait une référence à une autre bibliothèque de types qui n’est pas référencée avec `#import`. Cet autre fichier .tlb est introuvable par le compilateur.

Notez que le compilateur ne recherche pas de bibliothèques de types dans des répertoires différents si vous utilisez le [/I (autres répertoires Include)](../../build/reference/i-additional-include-directories.md) option du compilateur pour spécifier ces répertoires. Si vous souhaitez que le compilateur recherche des bibliothèques de types dans des répertoires différents, ajoutez ces répertoires à la variable d’environnement PATH.

Par défaut, cet avertissement est émis en tant qu’erreur. C4772 ne peut pas être supprimée avec/W0.

## <a name="example"></a>Exemple

Il s’agit de la première bibliothèque de types nécessaire pour reproduire l’erreur C4772.

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

Il s’agit de la bibliothèque de types deuxième nécessaire pour reproduire l’erreur C4772.

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

L’exemple suivant génère l’erreur C4772 :

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```