---
title: Erreur du compilateur C3006 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3006
dev_langs:
- C++
helpviewer_keywords:
- C3006
ms.assetid: 449082ec-fd45-4c47-8ab3-ba6a719e4dc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 098a39fa6a2918a6a168c28ce322544fe944a1c6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103170"
---
# <a name="compiler-error-c3006"></a>Erreur du compilateur C3006

'clause' : un argument attendu est manquant dans la clause de la directive 'directive' OpenMP

Une directive OpenMP ne possède pas un argument attendu.

L’exemple suivant génère l’erreur C3006 :

```
// C3006.c
// compile with: /openmp
int main()
{
   #pragma omp parallel shared   // C3006
   // Try the following line instead:
   // #pragma omp parallel shared(x) {}

}
```