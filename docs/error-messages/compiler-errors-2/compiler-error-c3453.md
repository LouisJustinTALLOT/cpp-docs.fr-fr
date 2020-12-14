---
description: 'En savoir plus sur : erreur du compilateur C3453'
title: Erreur du compilateur C3453
ms.date: 11/04/2016
f1_keywords:
- C3453
helpviewer_keywords:
- C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
ms.openlocfilehash: 2ff1c246dc66d60266f0fc44e134db3ab21605df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315970"
---
# <a name="compiler-error-c3453"></a>Erreur du compilateur C3453

'attribut' : attribut non appliqué, car le qualificateur 'assembly' ne correspond pas

Les attributs de niveau assembly ou module peuvent uniquement être spécifiés comme des instructions autonomes.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3453 :

```cpp
// C3453.cpp
// compile with: /clr /c
[assembly:System::CLSCompliant(true)]   // C3453
// try the following line instead
// [assembly:System::CLSCompliant(true)];
ref class X {};
```
