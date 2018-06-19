---
title: Erreur du compilateur C2870 | Documents Microsoft
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
ms.openlocfilehash: 5fe9f47a96422493d6d731a18add8c23ff683f14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243487"
---
# <a name="compiler-error-c2870"></a>Erreur du compilateur C2870
'nom' : une définition de l’espace de noms doit apparaître soit au niveau de la portée du fichier soit immédiatement au sein d’une autre définition de l’espace de noms  
  
 Vous avez défini l’espace de noms `name` incorrectement. Espaces de noms doit être définie dans la portée du fichier (à l’extérieur de tous les blocs et classes) ou immédiatement au sein d’un autre espace de noms.  
  
 L’exemple suivant génère l’erreur C2870 :  
  
```  
// C2870.cpp  
// compile with: /c  
int main() {  
   namespace A { int i; };   // C2870  
}  
```