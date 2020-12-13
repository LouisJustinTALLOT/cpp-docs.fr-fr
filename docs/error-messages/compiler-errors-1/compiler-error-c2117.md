---
description: 'En savoir plus sur : erreur du compilateur C2117'
title: Erreur du compilateur C2117
ms.date: 11/04/2016
f1_keywords:
- C2117
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
ms.openlocfilehash: 0e0d84a73d5f36f3014aa07d51b9701276a6e071
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335252"
---
# <a name="compiler-error-c2117"></a>Erreur du compilateur C2117

'identificateur' : dépassement des limites d’un tableau

Un tableau a trop d’initialiseurs :

- Les éléments de tableau et les initialiseurs ne correspondent pas à la taille et à la quantité.

- Aucun espace pour la marque de fin null dans une chaîne.

L’exemple suivant génère l’C2117 :

```cpp
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```
