---
title: Erreur du compilateur C3291
ms.date: 11/04/2016
f1_keywords:
- C3291
helpviewer_keywords:
- C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
ms.openlocfilehash: e3f20d7d7e63079ed9c7a078e9fc9eac06d32677
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781612"
---
# <a name="compiler-error-c3291"></a>Erreur du compilateur C3291

'default' : ne peut pas être le nom d'une propriété triviale

Une propriété triviale ne peut pas être nommée `default`. Pour plus d'informations, voir [property](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3291.

```
// C3291.cpp
// compile with: /clr /c
ref struct C {
   property System::String ^ default;   // C3291
   property System::String ^ Default;   // OK
};
```