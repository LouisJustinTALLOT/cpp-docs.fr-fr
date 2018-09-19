---
title: Erreur du compilateur C2262 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2262
dev_langs:
- C++
helpviewer_keywords:
- C2262
ms.assetid: 727d1c6e-53e8-40e5-b7b8-6a7ac2011727
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44e60bfcf00e3e01340c3df1b79004e84e93f56c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071443"
---
# <a name="compiler-error-c2262"></a>Erreur du compilateur C2262

'spécificateurs_attributs' : aucune version, culture ou architecture de processeur ne peut être spécifiée pour les déclarations InternalsVisible

L’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> n’a pas été spécifié correctement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2262 :

```
// C2262.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("assembly_name, version=1.2.3.7")];   // C2262
[assembly: InternalsVisibleTo("assembly_name ")];   // OK
```