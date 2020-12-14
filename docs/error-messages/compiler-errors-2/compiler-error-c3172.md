---
description: 'En savoir plus sur : erreur du compilateur C3172'
title: Erreur du compilateur C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: d8ce88960e725266723c3c37cd9bfbbbd342027b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242169"
---
# <a name="compiler-error-c3172"></a>Erreur du compilateur C3172

'module_name' : impossible de spécifier des attributs de idl_module différents dans un projet

[idl_module](../../windows/attributes/idl-module.md) attributs portant le même nom mais des `dllname` paramètres ou différents `version` ont été trouvés dans deux des fichiers d’une compilation. Un seul `idl_module` attribut unique peut être spécifié par compilation.

Des `idl_module` attributs identiques peuvent être spécifiés dans plusieurs fichiers de code source.

Par exemple, si les `idl_module` attributs suivants ont été trouvés :

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

Puis,

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

le compilateur génère C3172 (Notez les différentes valeurs de version).
