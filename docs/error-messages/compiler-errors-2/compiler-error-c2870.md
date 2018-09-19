---
title: Erreur du compilateur C2870 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2870
dev_langs:
- C++
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47101cbc2fb1be48ba54166b9c6ef99fc0c6c35e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073874"
---
# <a name="compiler-error-c2870"></a>Erreur du compilateur C2870

'name' : une définition de l’espace de noms doit apparaître soit au niveau de la portée du fichier, soit immédiatement au sein d’une autre définition de l’espace de noms

Vous avez défini l’espace de noms `name` incorrectement. Espaces de noms doit être définie dans la portée du fichier (en dehors de tous les blocs et classes) ou immédiatement au sein d’un autre espace de noms.

L’exemple suivant génère l’erreur C2870 :

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```