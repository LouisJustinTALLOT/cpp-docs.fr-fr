---
title: Compilateur avertissement (niveau 4) C4242 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4242
dev_langs:
- C++
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 623183e5ee54c995d624f47461c724ee8f4befae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217396"
---
# <a name="compiler-warning-level-4-c4242"></a>Avertissement du compilateur (niveau 4) C4242
'identificateur' : conversion de 'type1' en 'type2', perte possible de données  
  
 Les types sont différents. Conversion de type peut entraîner une perte de données. Le compilateur effectue la conversion de type.  
  
 Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
 Pour plus d’informations sur l’erreur C4242, consultez [erreurs de compilateur communes](/windows/desktop/WinProg64/common-compiler-errors).  
  
 L’exemple suivant génère l’erreur C4242 :  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```