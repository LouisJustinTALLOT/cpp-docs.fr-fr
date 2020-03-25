---
title: Avertissement du compilateur (niveau 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: 0ffc4c4aeb7d37ffa45f503a34fd369d36c00ce4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164207"
---
# <a name="compiler-warning-level-1-c4042"></a>Avertissement du compilateur (niveau 1) C4042

'identificateur' : classe de stockage incorrecte

La classe de stockage spécifiée ne peut pas être utilisée avec cet identificateur dans ce contexte. Le compilateur utilise la classe de stockage par défaut à la place :

- `extern`, si *identifier* est une fonction.

- **auto**, si *identifier* est un paramètre formel ou une variable locale.

- Aucune classe de stockage, si l' *identificateur* est une variable globale.

Cet avertissement peut être provoqué par la spécification d’une classe de stockage autre que **Register** dans une déclaration de paramètre.

L’exemple suivant génère l’C4042

```cpp
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```
