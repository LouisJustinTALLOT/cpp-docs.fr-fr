---
description: 'En savoir plus sur : erreur du compilateur C2825'
title: Erreur du compilateur C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: fa72f915a77ec26e6da402ae8ff87ee380f1838c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194577"
---
# <a name="compiler-error-c2825"></a>Erreur du compilateur C2825

var : doit être une classe ou un espace de noms lorsqu’il est suivi de' :: '

Une tentative infructueuse a été effectuée pour former un nom qualifié.

Par exemple, assurez-vous que votre code ne contient pas de déclaration de fonction où le nom de la fonction commence par ::.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2825 :

```cpp
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```
