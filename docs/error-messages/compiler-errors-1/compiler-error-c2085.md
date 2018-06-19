---
title: Erreur du compilateur C2085 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0fe489dbdd0934926a056bbc7e5539f40ca1ba8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169840"
---
# <a name="compiler-error-c2085"></a>Erreur du compilateur C2085
'identificateur' : pas dans la liste de paramètres formels  
  
 L’identificateur a été déclaré dans une définition de fonction, mais pas dans la liste de paramètres formels. (C ANSI seulement)  
  
 L’exemple suivant génère l’erreur C2085 :  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 Solution possible :  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 Sans le point-virgule, `func1()` ressemble à une définition de fonction, et non pas comme un prototype, donc `main` est défini dans `func1()`, erreur C2085 pour l’identificateur `main`.