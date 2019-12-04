---
title: Erreur du compilateur C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 3025dbf7c6bf4701218c2d9a956cae26d7180848
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757603"
---
# <a name="compiler-error-c3279"></a>Erreur du compilateur C3279

les spécialisations partielles et explicites, ainsi que les instanciations explicites des modèles de classe déclarés dans l'espace de noms cli sont interdites

L’espace de noms `cli` est défini par Microsoft et contient des pseudo-modèles. Le compilateur C++ Microsoft n’autorise pas les spécialisations explicites, partielles et définies par l’utilisateur, ainsi que les instanciations explicites des modèles de classe dans cet espace de noms.

L’exemple suivant génère l’erreur C3279 :

```cpp
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```
