---
title: Erreur du compilateur C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 602c9ca1051646fca2c5788c036354047fad2522
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599474"
---
# <a name="compiler-error-c3171"></a>Erreur du compilateur C3171

'module' : Impossible de spécifier des attributs de module différents dans un projet

[module](../../windows/module-cpp.md) attributs avec des listes de paramètres différentes ont été trouvés dans deux des fichiers d’une compilation. Un seul `module` attribut peut être spécifié par la compilation.

Identiques `module` attributs peuvent être spécifiés dans plusieurs fichiers de code source.

Par exemple, si les éléments suivants `module` attributs ont été trouvés :

```
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

Puis,

```
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

le compilateur génère l’erreur C3171 (Notez les valeurs de version différente).