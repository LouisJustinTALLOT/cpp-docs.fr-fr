---
description: 'En savoir plus sur : erreur du compilateur C3170'
title: Erreur du compilateur C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: c799d3c62b32e87aadd02b22f22bb20db25ff16b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242234"
---
# <a name="compiler-error-c3170"></a>Erreur du compilateur C3170

Impossible d’avoir des identificateurs de module différents dans un projet

des attributs de [module](../../windows/attributes/module-cpp.md) avec des noms différents ont été trouvés dans deux des fichiers d’une compilation. Un seul `module` attribut unique peut être spécifié par compilation.

Des `module` attributs identiques peuvent être spécifiés dans plusieurs fichiers de code source.

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
