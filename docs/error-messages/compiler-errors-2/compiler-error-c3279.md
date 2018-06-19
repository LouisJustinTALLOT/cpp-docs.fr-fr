---
title: Erreur du compilateur C3279 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a86f3dd637f84901559c4be8443a81425347237
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256820"
---
# <a name="compiler-error-c3279"></a>Erreur du compilateur C3279
les spécialisations partielles et explicites, ainsi que les instanciations explicites des modèles de classe déclarés dans l'espace de noms cli sont interdites  
  
 L’espace de noms `cli` est défini par Microsoft et contient des pseudo-modèles. Le compilateur Visual C++ n’autorise pas les spécialisations partielles et explicites définies par l’utilisateur, ni les instanciations de modèles de classe dans cet espace de noms.  
  
 L’exemple suivant génère l’erreur C3279 :  
  
```  
// C3279.cpp  
// compile with: /clr  
namespace cli {  
   template <> ref class array<int> {};   // C3279  
   template <typename T> ref class array<T, 2> {};   // C3279  
}  
```