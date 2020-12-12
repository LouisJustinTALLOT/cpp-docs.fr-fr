---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1237'
title: Erreur des outils Éditeur de liens LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: ba6a0d23eea4d8d555115950fcd54a5e4f6a8bde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193980"
---
# <a name="linker-tools-error-lnk1237"></a>Erreur des outils Éditeur de liens LNK1237

pendant la génération du code, le compilateur a introduit une référence au symbole’Symbol’défini dans le module’module’compilé avec/GL

Au cours de la génération du code, le compilateur ne doit pas introduire de symboles qui seront résolus ultérieurement en définitions compilées **/GL**. `symbol` est un symbole qui a été introduit et résolu ultérieurement en une définition compilée avec **/GL**.

Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md).

Pour résoudre LNK1237, ne compilez pas le symbole avec **/GL** ou utilisez [/include (forcer les références de symboles)](../../build/reference/include-force-symbol-references.md) pour forcer une référence au symbole.

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK1237. Pour résoudre cette erreur, n’initialisez pas le tableau dans LNK1237_a. cpp et ajoutez **/include : __chkstk** à la commande Link.

```cpp
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```cpp
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```
