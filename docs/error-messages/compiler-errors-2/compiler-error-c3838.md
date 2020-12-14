---
description: 'En savoir plus sur : erreur du compilateur C3838'
title: Erreur du compilateur C3838
ms.date: 11/04/2016
f1_keywords:
- C3838
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
ms.openlocfilehash: 9ea5f250b7a881ab9be6724f84dac418eefc705e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249143"
---
# <a name="compiler-error-c3838"></a>Erreur du compilateur C3838

héritage explicite impossible à partir de’type'

Le spécifié `type` ne peut pas agir en tant que classe de base dans une classe.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3838 :

```cpp
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
