---
description: 'En savoir plus sur : erreur du compilateur C3291'
title: Erreur du compilateur C3291
ms.date: 11/04/2016
f1_keywords:
- C3291
helpviewer_keywords:
- C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
ms.openlocfilehash: 4fcaa080167ae8ef63ffd7b1b180a74e29ac6411
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144740"
---
# <a name="compiler-error-c3291"></a>Erreur du compilateur C3291

'default' : ne peut pas être le nom d'une propriété triviale

Une propriété triviale ne peut pas être nommée **`default`** . Pour plus d’informations, consultez [property](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3291.

```cpp
// C3291.cpp
// compile with: /clr /c
ref struct C {
   property System::String ^ default;   // C3291
   property System::String ^ Default;   // OK
};
```
