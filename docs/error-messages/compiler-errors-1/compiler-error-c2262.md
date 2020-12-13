---
description: 'En savoir plus sur : erreur du compilateur C2262'
title: Erreur du compilateur C2262
ms.date: 11/04/2016
f1_keywords:
- C2262
helpviewer_keywords:
- C2262
ms.assetid: 727d1c6e-53e8-40e5-b7b8-6a7ac2011727
ms.openlocfilehash: ef4cbeeeef9a7df42510dbf4cd021dde2081d294
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134574"
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
