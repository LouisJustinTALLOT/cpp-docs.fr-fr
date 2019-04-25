---
title: Erreur des outils Éditeur de liens LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: 380df2bff305acc47e423d69ea702d77c4eafdfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160430"
---
# <a name="linker-tools-error-lnk1313"></a>Erreur des outils Éditeur de liens LNK1313

> module ijw/native détecté ; liaison impossible avec des modules pure

## <a name="remarks"></a>Notes

La version actuelle de Visual C++ ne prend pas en charge la liaison de fichiers .obj de managées/natives natif ou mixte avec les fichiers .obj compilés avec **/CLR : pure**.

Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

## <a name="example"></a>Exemple

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>Exemple

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur LNK1313.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```