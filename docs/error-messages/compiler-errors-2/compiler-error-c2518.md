---
description: 'En savoir plus sur : erreur du compilateur C2518'
title: Erreur du compilateur C2518
ms.date: 11/04/2016
f1_keywords:
- C2518
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
ms.openlocfilehash: 1ebc270cd3544dc50d051677faeeec8e8e6bd979
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212725"
---
# <a name="compiler-error-c2518"></a>Erreur du compilateur C2518

mot clé’keyword’non conforme dans la liste de classes de base ; pas

Les mots clés **`class`** et ne **`struct`** doivent pas apparaître dans une liste de classes de base.

L’exemple suivant génère l’C2518 :

```cpp
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```
