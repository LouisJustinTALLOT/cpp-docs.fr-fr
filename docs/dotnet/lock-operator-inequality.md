---
title: lock::operator!=
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- lock.operator!=
- msclr.lock.operator!=
- msclr::lock::operator!=
- lock::operator!=
helpviewer_keywords:
- lock::operator!=
ms.assetid: ed1d674e-9ee9-4257-8a7e-2e3567d50222
ms.openlocfilehash: 5f202d6e7cc4c023b366f370ec2c419336822964
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558442"
---
# <a name="lockoperator"></a>lock::operator!=

Opérateur d’inégalité.

## <a name="syntax"></a>Syntaxe

```
template<class T> bool operator!=(
   T t
);
```

#### <a name="parameters"></a>Paramètres

*t*<br/>
L’objet pour lequel comparer l’inégalité.

## <a name="return-value"></a>Valeur de retour

Retourne **true** si `t` diffère, objet du verrou, **false** dans le cas contraire.

## <a name="example"></a>Exemple

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>Voir aussi

[lock, membres](../dotnet/lock-members.md)<br/>
[lock::operator==](../dotnet/lock-operator-equality.md)