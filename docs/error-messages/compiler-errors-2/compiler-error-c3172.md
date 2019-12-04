---
title: Erreur du compilateur C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 1da2676d660d23e3fb71b56263779b1f1edacbf9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761736"
---
# <a name="compiler-error-c3172"></a>Erreur du compilateur C3172

'module_name' : impossible de spécifier des attributs de idl_module différents dans un projet

[idl_module](../../windows/idl-module.md) des attributs portant le même nom mais des paramètres `dllname` ou `version` différents ont été trouvés dans deux des fichiers d’une compilation. Un seul attribut `idl_module` unique peut être spécifié par compilation.

Des attributs de `idl_module` identiques peuvent être spécifiés dans plusieurs fichiers de code source.

Par exemple, si les attributs `idl_module` suivants ont été trouvés :

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
