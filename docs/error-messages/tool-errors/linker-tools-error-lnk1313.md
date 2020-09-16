---
title: Erreur des outils Éditeur de liens LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: 03ff61a1f3501b3ea106138e957a657ed064e645
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683440"
---
# <a name="linker-tools-error-lnk1313"></a>Erreur des outils Éditeur de liens LNK1313

> module ijw/native détecté ; liaison impossible avec des modules pure

## <a name="remarks"></a>Notes

La version actuelle de Visual C++ ne prend pas en charge la liaison de fichiers. obj managés ou natifs natifs ou mixtes avec des fichiers. obj compilés avec **/clr : pure**.

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

## <a name="examples"></a>Exemples

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

L'exemple suivant génère l'erreur LNK1313.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
