---
title: Erreur du compilateur C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: a3af19fa6b4f4def9bb42325f648109cfafcdaef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761749"
---
# <a name="compiler-error-c3171"></a>Erreur du compilateur C3171

'module' : impossible de spécifier des attributs de module différents dans un projet

les attributs de [module](../../windows/module-cpp.md) avec différentes listes de paramètres ont été trouvés dans deux des fichiers d’une compilation. Un seul attribut `module` unique peut être spécifié par compilation.

Des attributs de `module` identiques peuvent être spécifiés dans plusieurs fichiers de code source.

Par exemple, si les attributs `module` suivants ont été trouvés :

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

Puis,

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

le compilateur génère C3171 (Notez les différentes valeurs de version).
