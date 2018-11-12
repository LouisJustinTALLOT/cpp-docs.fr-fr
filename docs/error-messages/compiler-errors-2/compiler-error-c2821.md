---
title: Erreur du compilateur C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: 5c725d9648a7800c68a2fbff20e594a400c296c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632545"
---
# <a name="compiler-error-c2821"></a>Erreur du compilateur C2821

premier paramètre formel de 'operator new' doit être 'unsigned int'

Le premier paramètre formel de le [opérateur new](../../standard-library/new-operators.md#op_new) doit être non signée `int`.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2821 :

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```