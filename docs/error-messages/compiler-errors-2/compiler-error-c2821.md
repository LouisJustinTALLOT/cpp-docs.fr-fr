---
description: 'En savoir plus sur : erreur du compilateur C2821'
title: Erreur du compilateur C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: c21c9dc0b1413292e1d73b6448ed008d6fc9a64d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194694"
---
# <a name="compiler-error-c2821"></a>Erreur du compilateur C2821

le premier paramètre formel de’operator new’doit être’unsigned int'

Le premier paramètre formel de l' [opérateur New](../../standard-library/new-operators.md#op_new) doit être un non signé **`int`** .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2821 :

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```
