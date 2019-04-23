---
title: Avertissement du compilateur (niveau 1) C4688
ms.date: 11/04/2016
f1_keywords:
- C4688
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
ms.openlocfilehash: 1c94198eca0a88174c8655e0d571c37f82a2df36
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777548"
---
# <a name="compiler-warning-level-1-c4688"></a>Avertissement du compilateur (niveau 1) C4688

'constraint' : la liste des contraintes contient un type privé d’assembly 'type'

Une liste de contraintes possède un type privé d’assembly, ce qui signifie qu’il ne sera pas accessible en dehors de l’assembly. Pour plus d’informations, consultez la page [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4688.

```
// C4688.cpp
// compile with: /clr /c /W1
ref struct A {};   // private type
public ref struct B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C4688
public ref struct M {};

generic <class T>
where T : B
public ref struct N {};
```