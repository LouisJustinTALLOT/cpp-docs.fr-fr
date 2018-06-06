---
title: LNK4224 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bdffdf3469cc3a0e5d41b0504b882513d44b63c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703985"
---
# <a name="linker-tools-warning-lnk4224"></a>Avertissement des outils Éditeur de liens LNK4224

> *option* n’est plus pris en charge ; ignoré

## <a name="remarks"></a>Notes

Une option de l’éditeur de liens obsolètes, non valide a été spécifiée et est ignorée.

Par exemple, LNK4224 peut se produire si une directive /comment apparaît dans. obj. La directive /comment aurait été ajoutée via les [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md) pragma, à l’aide de l’option exestr déconseillée. Utilisez dumpbin [/tous les](../../build/reference/all.md) pour afficher les directives de l’éditeur de liens dans un fichier .obj.

Si possible, modifiez la source pour le fichier .obj et supprimez le pragma. Si vous ignorez cet avertissement, il est possible qu’un .executable compilé avec **/CLR : pure** ne fonctionnera pas comme prévu. Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK4224.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```