---
description: 'En savoir plus sur : erreur du compilateur C2810'
title: Erreur du compilateur C2810
ms.date: 11/04/2016
f1_keywords:
- C2810
helpviewer_keywords:
- C2810
ms.assetid: f63e8f24-d7f6-42ac-904f-72ff49592ba6
ms.openlocfilehash: 609a1ccd89619ddb66b42a81cf9a769480670508
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320585"
---
# <a name="compiler-error-c2810"></a>Erreur du compilateur C2810

'interface' : une interface ne peut hériter que d’une autre interface

Une [interface](../../cpp/interface.md) peut uniquement hériter d’une autre interface et ne peut pas hériter d’une classe ou d’un struct.

L’exemple suivant génère l’C2810 :

```cpp
// C2810.cpp
#include <unknwn.h>
class CBase1 {
public:
  HRESULT mf1();
  int  m_i;
};

[object, uuid="40719E20-EF37-11D1-978D-0000F805D73B"]
__interface IDerived : public CBase1 {  // C2810
// try the following line instead
// __interface IDerived {
   HRESULT mf2(void *a);
};

struct CBase2 {
   HRESULT mf1(int a, char *b);
   HRESULT mf2();
};
```
