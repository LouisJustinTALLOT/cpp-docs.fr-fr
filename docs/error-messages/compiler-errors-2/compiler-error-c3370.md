---
title: Erreur du compilateur C3370 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3370
dev_langs:
- C++
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 427a389de4d391cea059b5b7ef601016dea98d2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256445"
---
# <a name="compiler-error-c3370"></a>Erreur du compilateur C3370
'idl_module name' : module idl_module non encore défini  
  
 Avant de pouvoir utiliser [idl_module](../../windows/idl-module.md) pour spécifier un point d’entrée dans une DLL, vous devez d’abord utiliser `idl_module` pour spécifier le nom de la DLL.  
  
 L’exemple suivant génère l’erreur C3370 :  
  
```  
// C3370.cpp  
[module(name=MyLibrary)];  
// uncomment the following line to resolve the error  
// [idl_module(name="name1", dllname=x.dll)];  
[idl_module(name="name1"), entry(100)] // C3370  
int f1();  
  
int main()  
{  
}  
```