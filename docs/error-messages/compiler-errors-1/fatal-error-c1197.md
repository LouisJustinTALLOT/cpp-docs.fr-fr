---
title: Erreur irrécupérable C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: e1c00a001c807b0cc6a5946b61ca4e9d5dc0167a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229119"
---
# <a name="fatal-error-c1197"></a>Erreur irrécupérable C1197

Impossible de référencer 'mscorlib.dll_1 ', car le programme a déjà référencé 'mscorlib.dll_2'

Le compilateur ne correspond à une version du common language runtime.  Toutefois, une tentative a été effectuée pour référencer une version d’un fichier du common language runtime à partir d’une version précédente.

Pour résoudre cette erreur, référencer uniquement des fichiers à partir de la version du common language runtime fourni avec la version de Visual C++ que vous compilez avec.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C1197 :

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```