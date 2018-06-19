---
title: Erreur LNK1237 des outils Éditeur de liens | Documents Microsoft
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
ms.openlocfilehash: 1ffc337d6b1548db4717dc4b87ff8aa25ef92e93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298614"
---
# <a name="linker-tools-error-lnk1237"></a>Erreur des outils Éditeur de liens LNK1237
pendant la génération de code, du compilateur a introduit une référence au symbole 'symbole' défini dans le module 'module' compilé avec /GL  
  
 Pendant la génération de code, le compilateur ne doit pas introduire les symboles qui sont résolus ultérieurement en définitions compilées **/GL**. `symbol` est un symbole qui a été introduit et résolu ultérieurement en une définition compilée avec **/GL**.  
  
 Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md).  
  
 Pour résoudre l’erreur LNK1237, ne compilez pas le symbole avec **/GL** ou utilisez [/INCLUDE (forcer les références de symboles)](../../build/reference/include-force-symbol-references.md) pour forcer une référence au symbole.  
  
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