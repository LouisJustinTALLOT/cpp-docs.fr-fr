---
title: Erreur du compilateur C2026 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6b2952daa8cc7b3642cca5ba278990fde7d1ebe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167663"
---
# <a name="compiler-error-c2026"></a>Erreur du compilateur C2026
chaîne trop grande, caractères de fin tronqués  
  
 La chaîne était supérieure à la limite de 16380 caractères codés sur un octet.  
  
 Avant la concaténation des chaînes adjacentes, une chaîne ne peut pas dépasser 16380 caractères codés sur un octet.  
  
 Une chaîne Unicode d’environ la moitié de cette longueur générerait également cette erreur.  
  
 Si vous avez une chaîne définie comme suit, il génère C2026 :  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 Vous pourriez la fractionner comme suit :  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 Vous pouvez vouloir stocker des littéraux de chaîne de taille exceptionnelle (32 Ko ou plus) dans une ressource personnalisée ou d’un fichier externe. Consultez [création d’une ressource personnalisée ou ressource de données](../../windows/creating-a-new-custom-or-data-resource.md) pour plus d’informations.