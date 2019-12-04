---
title: Erreur irrécupérable C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: 7f698262c73f0b311a92a8940107b552430919bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747239"
---
# <a name="fatal-error-c1197"></a>Erreur irrécupérable C1197

Impossible de référencer’mscorlib. dll_1 ', car le programme a déjà référencé’mscorlib. dll_2 '

Le compilateur est mis en correspondance avec une version du common language runtime.  Toutefois, une tentative de référencement d’une version d’un fichier common language runtime à partir d’une version antérieure a été effectuée.

Pour résoudre cette erreur, utilisez uniquement les fichiers de référence de la version de la common language runtime fournie avec la version C++ de Visual avec laquelle vous effectuez la compilation.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C1197 :

```cpp
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
