---
title: Erreur des outils Éditeur de liens LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: c75966d9c6c22f1bd2123fb30282bb2bed467130
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991031"
---
# <a name="linker-tools-error-lnk1107"></a>Erreur des outils Éditeur de liens LNK1107

fichier non valide ou endommagé : impossible de lire à l’emplacement

L’outil n’a pas pu lire le fichier. Recréez le fichier.

LNK1107 peut également se produire si vous tentez de passer un module (extension. dll ou. netmodule créé avec [/clr : noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) ou [/noAssembly](../../build/reference/noassembly-create-a-msil-module.md)) à l’éditeur de liens ; transmettez le fichier. obj à la place.

Si vous compilez l’exemple suivant :

```cpp
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

et que vous spécifiez le **lien LNK1107. dll** sur la ligne de commande, vous obtiendrez LNK1107.  Pour résoudre l’erreur, spécifiez **Link LNK1107. obj** à la place.
