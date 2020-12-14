---
description: 'En savoir plus sur : erreur du compilateur C3171'
title: Erreur du compilateur C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 65e7e1db9a864b894a0bce825df09a372489a79d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242195"
---
# <a name="compiler-error-c3171"></a>Erreur du compilateur C3171

'module' : impossible de spécifier des attributs de module différents dans un projet

les attributs de [module](../../windows/attributes/module-cpp.md) avec différentes listes de paramètres ont été trouvés dans deux des fichiers d’une compilation. Un seul `module` attribut unique peut être spécifié par compilation.

Des `module` attributs identiques peuvent être spécifiés dans plusieurs fichiers de code source.

Par exemple, si les `module` attributs suivants ont été trouvés :

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
