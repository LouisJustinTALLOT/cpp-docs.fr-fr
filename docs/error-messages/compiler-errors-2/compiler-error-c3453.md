---
title: Erreur du compilateur C3453
ms.date: 11/04/2016
f1_keywords:
- C3453
helpviewer_keywords:
- C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
ms.openlocfilehash: 2b3288d02c611bf6785ca1ea7757e2283d889050
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328628"
---
# <a name="compiler-error-c3453"></a>Erreur du compilateur C3453

'attribut' : attribut non appliqué, car le qualificateur 'assembly' ne correspond pas

Les attributs de niveau assembly ou module peuvent uniquement être spécifiés comme des instructions autonomes.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3453 :

```
// C3453.cpp
// compile with: /clr /c
[assembly:System::CLSCompliant(true)]   // C3453
// try the following line instead
// [assembly:System::CLSCompliant(true)];
ref class X {};
```