---
title: Erreur du compilateur C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: a4c51ccfc724cf8309044812b287677f0f1a2ff0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754899"
---
# <a name="compiler-error-c3846"></a>Erreur du compilateur C3846

'Symbol' : impossible d’importer le symbole de’Assembly2 ', car’Symbol’a déjà été importé à partir d’un autre assembly’Assembly1 '

Impossible d’importer un symbole à partir d’un assembly référencé, car il a été importé précédemment à partir d’un assembly référencé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3846 :

```cpp
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

Puis compilez ce qui suit :

```cpp
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
