---
title: Erreur LNK1237 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9ada38fcf3a706f7852f49f60f677fb5dc10d7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065294"
---
# <a name="linker-tools-error-lnk1237"></a>Erreur des outils Éditeur de liens LNK1237

pendant la génération du code, du compilateur a introduit une référence au symbole 'symbole' défini dans le module 'module' compilé avec /GL

Pendant la génération de code, le compilateur ne doit pas introduire symboles résolus ultérieurement aux définitions compilées **/GL**. `symbol` est un symbole qui a été introduit et résolu ultérieurement en une définition compilée avec **/GL**.

Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md).

Pour résoudre l’erreur LNK1237, ne compilez pas le symbole avec **/GL** ou utilisez [/INCLUDE (forcer les références des symboles)](../../build/reference/include-force-symbol-references.md) pour forcer une référence au symbole.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK1237. Pour résoudre cette erreur, ne pas initialiser le tableau dans LNK1237_a.cpp et ajoutez **/ include : __chkstk** à la commande de lien.

```
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```