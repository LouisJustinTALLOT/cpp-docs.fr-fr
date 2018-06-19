---
title: Compilateur avertissement (niveau 1) C4628 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4628
dev_langs:
- C++
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffc84b8b7ec9934bb0dae951f5868d271ab62be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281679"
---
# <a name="compiler-warning-level-1-c4628"></a>Avertissement du compilateur (niveau 1) C4628
digrammes non pris en charge avec -Ze. Séquence de caractères 'digramme' non interprétée comme jeton de remplacement pour 'car'  
  
 Digrammes ne sont pas pris en charge sous [/Ze](../../build/reference/za-ze-disable-language-extensions.md). Cet avertissement est suivi d’une erreur.  
  
 Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
 L’exemple suivant génère l’erreur C4628 :  
  
```  
// C4628.cpp  
// compile with: /WX  
#pragma warning(default : 4628)  
int main()  
<%   // C4628 <% digraph for {  
}  
```