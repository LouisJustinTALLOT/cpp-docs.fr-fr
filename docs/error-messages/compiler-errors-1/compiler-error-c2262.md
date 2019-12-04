---
title: Erreur du compilateur C2262
ms.date: 11/04/2016
f1_keywords:
- C2262
helpviewer_keywords:
- C2262
ms.assetid: 727d1c6e-53e8-40e5-b7b8-6a7ac2011727
ms.openlocfilehash: e8723c03d37c04a5b99dc4b30cd2604718369c49
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758760"
---
# <a name="compiler-error-c2262"></a>Erreur du compilateur C2262

'spécificateurs_attributs' : aucune version, culture ou architecture de processeur ne peut être spécifiée pour les déclarations InternalsVisible

L’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> n’a pas été spécifié correctement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2262 :

```cpp
// C2262.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("assembly_name, version=1.2.3.7")];   // C2262
[assembly: InternalsVisibleTo("assembly_name ")];   // OK
```
