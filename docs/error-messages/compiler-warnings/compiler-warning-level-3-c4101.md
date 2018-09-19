---
title: Compilateur avertissement (niveau 3) C4101 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4101
dev_langs:
- C++
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1549a327329d438cb30bd6908e07419eb1b6bc1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060835"
---
# <a name="compiler-warning-level-3-c4101"></a>Compilateur avertissement (niveau 3) C4101

'identificateur' : variable locale non référencée

La variable locale n’est jamais utilisée. Cet avertissement se produit dans la situation évidente :

```
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

Toutefois, cet avertissement se produit également lorsque vous appelez un **statique** fonction membre via une instance de la classe :

```
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

Dans ce cas, le compilateur utilise les informations sur les `si` pour accéder à la **statique** (fonction), mais l’instance de la classe n’est pas nécessaire d’appeler le **statique** fonction ; par conséquent, l’avertissement. Pour résoudre cet avertissement, vous pouvez :

- Ajoutez un constructeur, dans lequel le compilateur utilise l’instance de `si` dans l’appel à `func`.

- Supprimer le **statique** mot clé à partir de la définition de `func`.

- Appelez le **statique** fonction explicitement : `int y = S::func();`.