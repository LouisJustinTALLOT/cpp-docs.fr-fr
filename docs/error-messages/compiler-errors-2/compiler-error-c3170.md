---
title: Erreur du compilateur C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: 5ef39e4580601dd90b5695d9115902bb5b834409
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174703"
---
# <a name="compiler-error-c3170"></a>Erreur du compilateur C3170

ne peut pas avoir des identificateurs de module différents dans un projet

[module](../../windows/module-cpp.md) attributs avec des noms différents ont été trouvés dans deux des fichiers d’une compilation. Un seul `module` attribut peut être spécifié par la compilation.

Identiques `module` attributs peuvent être spécifiés dans plusieurs fichiers de code source.

Par exemple, si les attributs de module suivants ont été trouvés :

```
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

Puis,

```
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

le compilateur générerait C3170 (Notez les noms différents).