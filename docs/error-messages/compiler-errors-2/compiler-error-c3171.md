---
title: Erreur du compilateur C3171 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32c58f2ecd9651c347f45c29139ffe0ed65a6e3b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082259"
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