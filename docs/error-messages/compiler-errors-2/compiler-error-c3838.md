---
title: Erreur du compilateur C3838
ms.date: 11/04/2016
f1_keywords:
- C3838
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
ms.openlocfilehash: 468fc5e8cb6b3a76880f12fe0aab14810f458a90
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741350"
---
# <a name="compiler-error-c3838"></a>Erreur du compilateur C3838

héritage explicite impossible à partir de’type'

La `type` spécifiée ne peut pas agir en tant que classe de base dans une classe.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3838 :

```cpp
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
