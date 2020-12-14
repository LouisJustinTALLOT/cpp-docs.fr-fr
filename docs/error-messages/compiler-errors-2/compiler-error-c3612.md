---
description: 'En savoir plus sur : erreur du compilateur C3612'
title: Erreur du compilateur C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: 332d4bae940a0c98b148fd6ba951a4f51d1bee27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223098"
---
# <a name="compiler-error-c3612"></a>Erreur du compilateur C3612

'type' : une classe sealed ne peut pas être abstract

Les types définis à l’aide de `value` sont sealed par défaut, et une classe est abstraite sauf si elle implémente toutes les méthodes de sa base. Une classe abstraite sealed ne peut pas être une classe de base et ne peut pas être instanciée.

Pour plus d’informations, consultez [Classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3612 :

```cpp
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```
