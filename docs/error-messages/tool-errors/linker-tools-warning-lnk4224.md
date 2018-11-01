---
title: Avertissement des outils Éditeur de liens LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: eb0a019cc80e5218a52697b8bcd5e91b811d04d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465323"
---
# <a name="linker-tools-warning-lnk4224"></a>Avertissement des outils Éditeur de liens LNK4224

> *option* n’est plus pris en charge ; ignoré

## <a name="remarks"></a>Notes

Une option de l’éditeur de liens obsolètes, non valide a été spécifiée et ignorée.

Par exemple, LNK4224 peut se produire si une directive /comment apparaît dans. obj. La directive /comment aurait été ajoutée via le [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md) pragma, à l’aide de l’option exestr déconseillée. Utilisez dumpbin [/ALL](../../build/reference/all.md) pour afficher les directives de l’éditeur de liens dans un fichier .obj.

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