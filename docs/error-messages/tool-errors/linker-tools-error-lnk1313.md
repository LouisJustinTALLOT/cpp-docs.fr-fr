---
title: Erreur des outils Éditeur de liens LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: a2314f160dc6add45547082c7804ec5e2c8f2349
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194861"
---
# <a name="linker-tools-error-lnk1313"></a>Erreur des outils Éditeur de liens LNK1313

> module ijw/native détecté ; liaison impossible avec des modules pure

## <a name="remarks"></a>Notes

La version actuelle de Visual C++ ne prend pas en charge la liaison de fichiers. obj managés ou natifs natifs ou mixtes avec des fichiers. obj compilés avec **/clr : pure**.

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

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
