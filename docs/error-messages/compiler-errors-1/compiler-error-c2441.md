---
title: Erreur du compilateur C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 7fcf333f62253eb676c0f0ada1c927ab962ae1ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551251"
---
# <a name="compiler-error-c2441"></a>Erreur du compilateur C2441

> «*variable*' : un symbole déclaré avec __declspec (Process) doit être const en/clr : pur mode

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Par défaut, les variables sont par domaine d’application sous **/CLR : pure**. Une variable marquée `__declspec(process)` sous **/CLR : pure** est sujette aux erreurs si modifié dans un domaine d’application et lues dans un autre.

Par conséquent, le compilateur applique variables par processus `const` sous **/CLR : pure**, apporter les lire uniquement dans tous les domaines d’application.

Pour plus d’informations, consultez [processus](../../cpp/process.md) et [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```