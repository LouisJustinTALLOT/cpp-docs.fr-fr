---
title: Erreur du compilateur C3457
ms.date: 11/04/2016
f1_keywords:
- C3457
helpviewer_keywords:
- C3457
ms.assetid: 5c1e366a-fa75-4cca-b9a3-86d4ebe4090e
ms.openlocfilehash: 1481bd1d430aff74bff8140941b0ab218acbe364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200880"
---
# <a name="compiler-error-c3457"></a>Erreur du compilateur C3457

'attribute' : l’attribut ne prend pas en charge les arguments sans nom

Les attributs d’annotations sources, contrairement à l’attribut CLR personnalisé ou aux attributs du compilateur, ne prennent en charge que les arguments nommés.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3457 :

```
#include "SourceAnnotations.h"
[vc_attributes::Post( 1 )] int f();   // C3457
[vc_attributes::Post( Valid=vc_attributes::Yes )] int f2();   // OK
```
