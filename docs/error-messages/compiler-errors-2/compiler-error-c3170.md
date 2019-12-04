---
title: Erreur du compilateur C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: e2d74a637e2902fcf636b49068882f32aa706f94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761762"
---
# <a name="compiler-error-c3170"></a>Erreur du compilateur C3170

Impossible d’avoir des identificateurs de module différents dans un projet

des attributs de [module](../../windows/module-cpp.md) avec des noms différents ont été trouvés dans deux des fichiers d’une compilation. Un seul attribut `module` unique peut être spécifié par compilation.

Des attributs de `module` identiques peuvent être spécifiés dans plusieurs fichiers de code source.

Par exemple, si les attributs de module suivants ont été trouvés :

```cpp
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

Puis,

```cpp
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

le compilateur génère C3170 (Notez les noms différents).
