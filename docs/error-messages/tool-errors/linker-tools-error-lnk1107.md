---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1107'
title: Erreur des outils Éditeur de liens LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: 2a5ed9ba0bc4789a324d143b6287a08712299cdd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281390"
---
# <a name="linker-tools-error-lnk1107"></a>Erreur des outils Éditeur de liens LNK1107

fichier non valide ou endommagé : impossible de lire à l’emplacement

L’outil n’a pas pu lire le fichier. Recréez le fichier.

LNK1107 peut également se produire si vous tentez de passer un module (extension. dll ou. netmodule créé avec [/clr : noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) ou  [/noAssembly](../../build/reference/noassembly-create-a-msil-module.md)) à l’éditeur de liens ; transmettez le fichier. obj à la place.

Si vous compilez l’exemple suivant :

```cpp
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

puis spécifiez le **lien LNK1107.dll** sur la ligne de commande, vous obtiendrez LNK1107.  Pour résoudre l’erreur, spécifiez **Link LNK1107. obj** à la place.
