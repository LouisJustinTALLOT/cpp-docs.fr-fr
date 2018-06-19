---
title: Compilateur avertissement (niveau 1) C4964 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98226b2da465d2301356939273d370d76edcb64e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290314"
---
# <a name="compiler-warning-level-1-c4964"></a>Avertissement du compilateur (niveau 1) C4964
Aucune option d’optimisation ont été spécifiées ; les informations de profil ne seront pas collectées.  
  
 [/GL](../../build/reference/gl-whole-program-optimization.md) et [LTCG](../../build/reference/ltcg-link-time-code-generation.md) ont été spécifiées, mais aucune optimisation n’a été demandé, donc aucun fichier .pgc ne sera généré et, par conséquent, aucune optimisation guidée par profil n’est plus possible.  
  
 Si vous souhaitez que les fichiers .pgc à générer lorsque vous exécutez votre application, spécifiez l’une de la [/O](../../build/reference/o-options-optimize-code.md) options du compilateur.  
  
 L’exemple suivant génère l’erreur C4964 :  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```