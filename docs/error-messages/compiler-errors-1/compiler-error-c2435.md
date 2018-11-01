---
title: Erreur du compilateur C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 5cd7a83575da7ab2a30401406d0c2ccf6c1b603e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438531"
---
# <a name="compiler-error-c2435"></a>Erreur du compilateur C2435

> «*var*' : l’initialisation dynamique requiert un CRT managé, Impossible de compiler avec/clr : safe

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

L’initialisation de variable globale de domaine par application exige la compilation du CRT avec `/clr:pure`, qui ne produit pas d’image vérifiable.

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2435 :

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```