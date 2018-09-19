---
title: Compilateur avertissement (niveau 4) C4625 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4625
dev_langs:
- C++
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 970321370aeeea0ca4324f9a25d3ee1d8e54e15e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069103"
---
# <a name="compiler-warning-level-4-c4625"></a>Avertissement du compilateur (niveau 4) C4625

'classe dérivée' : le constructeur de copie a été défini de manière implicite comme supprimé car un constructeur de copie de la classe de base est inaccessible ou supprimé

Un constructeur de copie a été supprimé ou n'était pas accessible dans une classe de base, et il n'a donc pas été généré pour une classe dérivée. Toute tentative pour copier un objet de ce type provoquera une erreur du compilateur.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C4625 et montre comment la corriger.

```
// C4625.cpp
// compile with: /W4 /c
#pragma warning(default : 4625)

struct A {
   A() {}

private:
   A(const A&) {}
};

struct C : private virtual A {};
struct B :  C {};   // C4625 no copy constructor

struct D : A {};
struct E :  D {};   // OK
```