---
title: Erreur du compilateur C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 5f39510ee9ec0e717d675aa8b396405bc33b4ea1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445004"
---
# <a name="compiler-error-c3279"></a>Erreur du compilateur C3279

les spécialisations partielles et explicites, ainsi que les instanciations explicites des modèles de classe déclarés dans l'espace de noms cli sont interdites

L’espace de noms `cli` est défini par Microsoft et contient des pseudo-modèles. Le compilateur Visual C++ n’autorise pas les spécialisations partielles et explicites définies par l’utilisateur, ni les instanciations de modèles de classe dans cet espace de noms.

L’exemple suivant génère l’erreur C3279 :

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```