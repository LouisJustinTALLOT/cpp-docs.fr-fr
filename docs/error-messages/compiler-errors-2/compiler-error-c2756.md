---
title: Erreur du compilateur C2756 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2756
dev_langs:
- C++
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3eb61cd111166867be0439709a8b73dd4056099
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231775"
---
# <a name="compiler-error-c2756"></a>Erreur du compilateur C2756
’type de modèle’ : les arguments template par défaut ne sont pas autorisés sur une spécialisation partielle  
  
 Le modèle pour une spécialisation partielle ne peut pas contenir d’argument par défaut.  
  
 L'exemple suivant génère l'erreur C2756 et montre comment la corriger :  
  
```  
// C2756.cpp  
template <class T>  
struct S {};  
  
template <class T=int>  
// try the following line instead  
// template <class T>  
struct S<T*> {};   // C2756  
```