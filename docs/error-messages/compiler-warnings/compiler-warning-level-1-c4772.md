---
title: Avertissement du compilateur (niveau 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 89156b2f29fd21160e6abddc3ecb21efaee6dde1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175128"
---
# <a name="compiler-warning-level-1-c4772"></a>Avertissement du compilateur (niveau 1) C4772

> \#importer référence un type à partir d’une bibliothèque de types manquante ; '*Missing-type*'utilisé en tant qu’espace réservé

Une bibliothèque de types a été référencée avec la directive [#import](../../preprocessor/hash-import-directive-cpp.md) . Toutefois, la bibliothèque de types contenait une référence à une autre bibliothèque de types qui n’a pas été référencée avec `#import`. Ce fichier. tlb est introuvable par le compilateur.

Notez que le compilateur ne trouvera pas les bibliothèques de types dans les différents répertoires si vous utilisez l’option de compilateur [/i (autres répertoires Include)](../../build/reference/i-additional-include-directories.md) pour spécifier ces répertoires. Si vous souhaitez que le compilateur trouve des bibliothèques de types dans des répertoires différents, ajoutez ces répertoires à la variable d’environnement PATH.

Par défaut, cet avertissement est émis en tant qu’erreur. C4772 ne peut pas être supprimé avec/W0.

## <a name="example"></a>Exemple

Il s’agit de la première bibliothèque de types nécessaire pour reproduire C4772.

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

Il s’agit de la deuxième bibliothèque de types nécessaire pour reproduire C4772.

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

L’exemple suivant génère l’C4772 :

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```
