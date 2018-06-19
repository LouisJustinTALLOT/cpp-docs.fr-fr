---
title: Erreur du compilateur C2348 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2348
dev_langs:
- C++
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9728b044d05374e46b685df385409ddc3cb614f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222239"
---
# <a name="compiler-error-c2348"></a>Erreur du compilateur C2348
'type name' : n’est pas un agrégat de style C, ne peut pas être exporté dans un IDL incorporé  
  
 Pour placer un `struct` dans un fichier .idl avec la [exporter](../../windows/export.md) attribut, la `struct` doit contenir uniquement des données.  
  
 L’exemple suivant génère l’erreur C2348 :  
  
```  
// C2348.cpp  
// C2348 error expected  
[ module(name="SimpleMidlTest") ];  
  
[export]  
struct Point {  
   // Delete the following two lines to resolve.  
   Point() : m_i(0), m_j(0) {}  
   Point(int i, int j) : m_i(i), m_j(j) {}  
  
   int m_i;  
   int m_j;  
};  
```