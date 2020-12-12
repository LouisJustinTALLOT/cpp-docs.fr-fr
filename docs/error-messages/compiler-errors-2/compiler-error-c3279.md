---
description: 'En savoir plus sur : erreur du compilateur C3279'
title: Erreur du compilateur C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: c257a97cad1603703e7dbf2ed0d9f5cb3e6134a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258016"
---
# <a name="compiler-error-c3279"></a>Erreur du compilateur C3279

les spécialisations partielles et explicites, ainsi que les instanciations explicites des modèles de classe déclarés dans l'espace de noms cli sont interdites

L’espace de noms `cli` est défini par Microsoft et contient des pseudo-modèles. Le compilateur Microsoft C++ n’autorise pas les spécialisations explicites, partielles et définies par l’utilisateur, ainsi que les instanciations explicites des modèles de classe dans cet espace de noms.

L’exemple suivant génère l’erreur C3279 :

```cpp
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```
