---
title: Erreur du compilateur C3612 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3612
dev_langs:
- C++
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16d960095942af34aa516341862c9a2bcf72bbba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053678"
---
# <a name="compiler-error-c3612"></a>Erreur du compilateur C3612

'type' : une classe sealed ne peut pas être abstract

Types définis à l’aide de `value` sont scellées par défaut, et une classe est abstraite, sauf si elle implémente toutes les méthodes de sa base. Une classe abstraite sealed ne peut ni être une classe de base ni être instanciée.

Pour plus d’informations, consultez [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3612 :

```
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```