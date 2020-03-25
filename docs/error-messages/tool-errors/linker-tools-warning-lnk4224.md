---
title: Avertissement des outils Éditeur de liens LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: 9e52dd533d897e729aba5f2b43ea6c019a024d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182979"
---
# <a name="linker-tools-warning-lnk4224"></a>Avertissement des outils Éditeur de liens LNK4224

> l' *option* n’est plus prise en charge ; pas

## <a name="remarks"></a>Notes

Une option d’éditeur de liens non valide et obsolète a été spécifiée et ignorée.

Par exemple, LNK4224 peut se produire si une directive/comment apparaît dans. obj. La directive/comment aurait été ajoutée via le pragma [Comment (C/C++)](../../preprocessor/comment-c-cpp.md) , à l’aide de l’option exestr déconseillée. Utilisez DUMPBIN [/All](../../build/reference/all.md) pour afficher les directives de l’éditeur de liens dans un fichier. obj.

Si possible, modifiez la source du. objet supprimez le pragma. Si vous ignorez cet avertissement, il est possible qu’un fichier. Executable compilé avec **/clr : pure** ne s’exécute pas comme prévu. L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK4224.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```
