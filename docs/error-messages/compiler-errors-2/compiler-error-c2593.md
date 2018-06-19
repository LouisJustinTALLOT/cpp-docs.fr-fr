---
title: Erreur du compilateur C2593 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e419416266e0e3c4ebff8190b3b26b1c43c9ba0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229883"
---
# <a name="compiler-error-c2593"></a>Erreur du compilateur C2593
'operator identificateur' est ambigu  
  
 Plusieurs opérateurs possibles est défini pour un opérateur surchargé.  
  
 Cette erreur peut être résolue si vous utilisez un cast explicite sur un ou plusieurs paramètres réels.  
  
 L’exemple suivant génère l’erreur C2593 :  
  
```  
// C2593.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
void operator+( X, X );  
void operator+( A, B );  
D d;  
  
int main() {  
   d +  d;         // C2593, D has an A, B, and X   
   (X)d + (X)d;    // OK, uses operator+( X, X )  
}  
```  
  
 Cette erreur peut être provoquée par la sérialisation d’une variable à virgule flottante à l’aide un `CArchive` objet. Le compilateur identifie le `<<` opérateur comme ambiguë. Seuls les types primitifs C++ des types qui `CArchive` peut sérialiser sont les types de taille fixe `BYTE`, `WORD`, `DWORD`, et `LONG`. Tous les types d’entier doivent être converties en un de ces types pour la sérialisation. Les types à virgule flottante doivent être archivés à l’aide de la `CArchive::Write()` fonction membre.  
  
 L’exemple suivant montre comment archiver une variable à virgule flottante (`f`) à archive `ar`:  
  
```  
ar.Write(&f, sizeof( float ));  
```