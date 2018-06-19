---
title: Erreur du compilateur C3839 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3839
dev_langs:
- C++
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbb5541e07d168df36bae83f81b7b8a8a7273665
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269512"
---
# <a name="compiler-error-c3839"></a>Erreur du compilateur C3839
impossible de changer l'alignement dans un type managé ou WinRT  
  
 L’alignement des variables dans gérés ou les types Windows Runtime est contrôlé par le CLR ou Windows Runtime et ne peut pas être modifié avec [aligner](../../cpp/align-cpp.md).  
  
 L'exemple suivant génère l'erreur C3839 :  
  
```  
// C3839a.cpp  
// compile with: /clr  
ref class C  
{  
public:  
   __declspec(align(32)) int m_j; // C3839  
};  
  
int main()  
{  
}  
```