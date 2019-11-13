---
title: Avertissement du compilateur (niveau 1) C4662
ms.date: 11/04/2016
f1_keywords:
- C4662
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
ms.openlocfilehash: ff8a2f73523802a7c62e999be00c77400fbc0f23
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051427"
---
# <a name="compiler-warning-level-1-c4662"></a>Avertissement du compilateur (niveau 1) C4662

instanciation explicite ; la classe de modèle 'identificateur1' n’a aucune définition pour spécialiser 'identificateur2'

La classe de modèle spécifiée a été déclarée, mais pas définie.

## <a name="example"></a>Exemple

```cpp
// C4662.cpp
// compile with: /W1 /LD
template<class T, int i> class MyClass; // no definition
template MyClass< int, 1>;              // C4662
```