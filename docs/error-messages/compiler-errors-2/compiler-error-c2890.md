---
description: 'En savoir plus sur : erreur du compilateur C2890'
title: Erreur du compilateur C2890
ms.date: 11/04/2016
f1_keywords:
- C2890
helpviewer_keywords:
- C2890
ms.assetid: 49147375-182c-42b1-b170-f475cd436d47
ms.openlocfilehash: 4df022147b9e8b199fa2aea45c3af88525375690
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337442"
---
# <a name="compiler-error-c2890"></a>Erreur du compilateur C2890

'classe' : une classe ref ne peut avoir qu’une seule classe de base sans interface

Une classe de référence ne peut avoir qu’une seule classe de base.

L’exemple suivant génère l’C2890 :

```cpp
// C2890.cpp
// compile with: /clr /c
ref class A {};
ref class B {};
ref class C : public A, public B {};   // C2890
ref class D : public A {};   // OK
```
