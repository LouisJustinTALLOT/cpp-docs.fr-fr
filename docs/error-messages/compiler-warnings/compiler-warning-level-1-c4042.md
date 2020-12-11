---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4042'
title: Avertissement du compilateur (niveau 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: 458d8460b71ac1b0d002b0127e3637cdfd6766ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160634"
---
# <a name="compiler-warning-level-1-c4042"></a>Avertissement du compilateur (niveau 1) C4042

'identificateur' : classe de stockage incorrecte

La classe de stockage spécifiée ne peut pas être utilisée avec cet identificateur dans ce contexte. Le compilateur utilise la classe de stockage par défaut à la place :

- **`extern`**, si *identifier* est une fonction.

- **`auto`**, si *identifier* est un paramètre formel ou une variable locale.

- Aucune classe de stockage, si l' *identificateur* est une variable globale.

Cet avertissement peut être provoqué par la spécification d’une classe de stockage autre que **`register`** dans une déclaration de paramètre.

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
