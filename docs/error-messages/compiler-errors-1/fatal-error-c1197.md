---
description: 'En savoir plus sur : erreur irrécupérable C1197'
title: Erreur irrécupérable C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: c61cbd71fa8f17dc787fd9ee5eabd0f073aafb39
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268169"
---
# <a name="fatal-error-c1197"></a>Erreur irrécupérable C1197

Impossible de référencer' mscorlib.dll_1 ', car le programme a déjà référencé' mscorlib.dll_2 '

Le compilateur est mis en correspondance avec une version du common language runtime.  Toutefois, une tentative de référencement d’une version d’un fichier common language runtime à partir d’une version antérieure a été effectuée.

Pour résoudre cette erreur, seuls les fichiers de référence de la version de la common language runtime fournie avec la version de Visual C++ vous compilez.

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
