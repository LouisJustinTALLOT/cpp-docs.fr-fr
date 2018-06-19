---
title: Erreur du compilateur C3282 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3282
dev_langs:
- C++
helpviewer_keywords:
- C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e417eedf70388f379f4e66cfabf3f295aefec069
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254407"
---
# <a name="compiler-error-c3282"></a>Erreur du compilateur C3282
paramètre générique listes peuvent uniquement apparaître sur géré ou WinRTclasses, structures ou fonctions  
  
 Une liste de paramètres génériques a été utilisée de façon incorrecte.  Pour plus d’informations, consultez la page [Génériques](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C3282 et montre comment la corriger.  
  
```  
// C3282.cpp  
// compile with: /clr /c  
generic <typename T> int x;   // C3282  
  
ref struct GC0 {  
   generic <typename T> int x;   // C3282  
};  
  
// OK  
generic <typename T>  
ref class M {};  
```