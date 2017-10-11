---
title: Erreur du compilateur C3208 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3208
dev_langs:
- C++
helpviewer_keywords:
- C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5078264a615aa3dd998e2e71f366e8062054e6d4
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3208"></a>Erreur du compilateur C3208
'function' : la liste de paramètres template pour le modèle de classe 'class' ne correspond pas à la liste de paramètres de modèle pour le paramètre template du modèle 'parameter'  
  
 Un paramètre template de modèle n’a pas le même nombre de paramètres template que le modèle de classe fourni.  
  
 L’exemple suivant génère l’erreur C3208 :  
  
```  
// C3208.cpp  
template <template <class T> class TT >  
int f();  
  
template <class T1, class T2>  
struct S;  
  
template <class T1>  
struct R;  
  
int i = f<S>();   // C3208  
// try the following line instead  
// int i = f<R>();  
```
