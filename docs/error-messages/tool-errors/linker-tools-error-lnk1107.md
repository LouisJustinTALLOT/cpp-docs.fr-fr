---
title: Erreur des outils Éditeur de liens LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: 68048d9f824283d002a4ea8b64d88f37bbeefc48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255390"
---
# <a name="linker-tools-error-lnk1107"></a>Erreur des outils Éditeur de liens LNK1107

fichier non valide ou endommagé : Impossible de lire à l’emplacement

L’outil n’a pas pu lire le fichier. Recréez le fichier.

L’erreur LNK1107 peut également se produire si vous essayez de passer un module (extension de fichier .dll ou .netmodule créée avec [/CLR : noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) ou [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)) à l’éditeur de liens ; passez à la place le fichier .obj.

Si vous compilez l’exemple suivant :

```
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

puis spécifiez **link LNK1107.dll** sur la ligne de commande, vous obtiendrez l’erreur LNK1107.  Pour résoudre l’erreur, spécifiez **link LNK1107.obj** à la place.