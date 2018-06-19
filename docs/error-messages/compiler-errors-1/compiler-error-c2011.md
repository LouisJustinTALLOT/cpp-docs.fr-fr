---
title: Erreur du compilateur C2011 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2011
dev_langs:
- C++
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 898a724f022a81f590ec1f8165de9752de6c1d0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166635"
---
# <a name="compiler-error-c2011"></a>Erreur du compilateur C2011
'identificateur' : redéfinition du type 'type'  
  
 L'identificateur était déjà défini comme `type`. Recherchez les redéfinitions de l'identificateur.  
  
 L'erreur C2011 peut aussi apparaître si vous importez un fichier d'en-tête ou une bibliothèque de types plusieurs fois dans le même fichier. Pour empêcher plusieurs inclusions des types définis dans un fichier d’en-tête, utilisez des protections de type include ou une `#pragma` [une fois](../../preprocessor/once.md) directive dans le fichier d’en-tête.  
  
 Si vous devez rechercher la déclaration initiale du type redéfini, vous pouvez utiliser la [/P](../../build/reference/p-preprocess-to-a-file.md) indicateur de compilateur pour générer la sortie prétraitée passée au compilateur. Vous pouvez utiliser les outils de recherche de texte pour rechercher des instances de l'identificateur redéfini dans le fichier de sortie.  
  
 L'exemple suivant génère l'erreur C2011 et montre une manière de la corriger :  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```