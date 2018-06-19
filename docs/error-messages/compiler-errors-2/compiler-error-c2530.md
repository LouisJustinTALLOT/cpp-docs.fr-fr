---
title: Erreur du compilateur C2530 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b226ef5ca0e839c745e13d4118264a69ca408db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229400"
---
# <a name="compiler-error-c2530"></a>Erreur du compilateur C2530
'identificateur' : les références doivent être initialisées  
  
 Vous devez initialiser une référence lorsqu’il a été déclaré, sauf si elle est déjà déclarée :  
  
-   Avec le mot clé [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
-   En tant que membre d’une classe, structure ou union (et il est initialisé dans le constructeur).  
  
-   En tant que paramètre dans une définition ou déclaration de fonction.  
  
-   En tant que type de retour d’une fonction.  
  
 L’exemple suivant génère l’erreur C2530 :  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```