---
title: Erreur du compilateur C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 5c9c1561b63c740b9f7f5d85b2bf3e04de2542c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175184"
---
# <a name="compiler-error-c3172"></a>Erreur du compilateur C3172

'nom_module' : Impossible de spécifier des attributs idl_module différents dans un projet

[idl_module](../../windows/idl-module.md) attributs ayant le même nom mais des `dllname` ou `version` paramètres ont été trouvés dans deux des fichiers d’une compilation. Un seul `idl_module` attribut peut être spécifié par la compilation.

Identiques `idl_module` attributs peuvent être spécifiés dans plusieurs fichiers de code source.

Par exemple, si les éléments suivants `idl_module` attributs ont été trouvés :

```
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

Puis,

```
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

le compilateur génère l’erreur C3172 (Notez les valeurs de version différente).