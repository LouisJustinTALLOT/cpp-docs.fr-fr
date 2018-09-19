---
title: L’erreur LNK1107 erreur des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1107
dev_langs:
- C++
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73a1643d10ea9adc6ac6979eb2de023593ba8d01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060705"
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