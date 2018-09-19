---
title: Erreur irrécupérable C1308 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1308
dev_langs:
- C++
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd778e95f3ace413dbeb409da3c4b2493208e8bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104180"
---
# <a name="fatal-error-c1308"></a>Erreur irrécupérable C1308

liaison des assemblys n’est pas pris en charge.

Un fichier .netmodule est autorisé comme entrée dans l’éditeur de liens, mais n’est pas un assembly. Cette erreur peut être générée lorsqu’une tentative est effectuée pour lier un assembly compilé avec `/clr:safe`.

Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).

L’exemple suivant génère l’erreur C1308 :

```
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

Et puis

```
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```