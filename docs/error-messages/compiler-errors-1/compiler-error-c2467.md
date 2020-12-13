---
description: 'En savoir plus sur : erreur du compilateur C2467'
title: Erreur du compilateur C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: fd5227e451208d848d631550da33999a4ebae8dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333824"
---
# <a name="compiler-error-c2467"></a>Erreur du compilateur C2467

Déclaration de’User-Defined-type’anonyme non conforme

Un type imbriqué défini par l’utilisateur a été déclaré. Il s’agit d’une erreur lors de la compilation du code source C avec l’option de compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) activée.

L’exemple suivant génère l’C2467 :

```c
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```
