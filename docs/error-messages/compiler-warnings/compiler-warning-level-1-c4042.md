---
title: Compilateur avertissement (niveau 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: 99f4f45aad82aa9898dad4cffb60b8e3311ddc9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152137"
---
# <a name="compiler-warning-level-1-c4042"></a>Compilateur avertissement (niveau 1) C4042

'identificateur' : classe de stockage incorrecte

La classe de stockage spécifié ne peut pas être utilisée avec cet identificateur dans ce contexte. Le compilateur utilise la classe de stockage par défaut à la place :

- `extern`, si *identificateur* est une fonction.

- **Auto**si *identificateur* est un paramètre formel ou une variable locale.

- Aucun stockage ne classe si *identificateur* est une variable globale.

Cet avertissement peut être dû à la spécification d’une classe de stockage autre que **inscrire** dans une déclaration de paramètre.

L’exemple suivant génère C4042

```
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```