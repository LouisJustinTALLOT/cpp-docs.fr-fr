---
description: 'En savoir plus sur : erreur du compilateur C2351'
title: Erreur du compilateur C2351
ms.date: 11/04/2016
f1_keywords:
- C2351
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
ms.openlocfilehash: ae8cf10cff4a345ee067519d250210f72e6690f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145481"
---
# <a name="compiler-error-c2351"></a>Erreur du compilateur C2351

syntaxe obsolète d’initialisation d’un constructeur C++

Dans une liste d’initialisation de nouveau style pour un constructeur, vous devez nommer explicitement chaque classe de base directe, même s’il s’agit de la seule classe de base.

L’exemple suivant génère l’C2351 :

```cpp
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```
