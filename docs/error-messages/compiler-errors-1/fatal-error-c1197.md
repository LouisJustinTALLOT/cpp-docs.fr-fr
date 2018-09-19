---
title: Erreur irrécupérable C1197 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1197
dev_langs:
- C++
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58561e7bd906fc750779ef53a4f68ec27088a3b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024760"
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