---
title: Erreur du compilateur C3747 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3747
dev_langs:
- C++
helpviewer_keywords:
- C3747
ms.assetid: a9a4be67-5d9c-4dcc-9ae9-baae46cbecde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ca36074f33299b1a55da0fe7b42786a05dd6c49
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264114"
---
# <a name="compiler-error-c3747"></a>Erreur du compilateur C3747
paramètre de type par défaut manquant : paramètre param  
  
 Paramètres génériques ou de modèle avec les valeurs par défaut ne peut pas être suivis dans la liste des paramètres par les paramètres qui n’ont pas de valeurs par défaut.  
  
 L’exemple suivant génère l’erreur C3747 :  
  
```  
// C3747.cpp  
template <class T1 = int, class T2>   // C3747  
struct MyStruct {};  
```  
  
 Solution possible :  
  
```  
// C3747b.cpp  
// compile with: /c  
template <class T1, class T2 = int>  
struct MyStruct {};  
```