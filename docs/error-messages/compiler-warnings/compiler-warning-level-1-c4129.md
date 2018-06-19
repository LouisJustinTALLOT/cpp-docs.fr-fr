---
title: Compilateur avertissement (niveau 1) C4129 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc095a32e5cb0d5a0bf240282e11c3fa3382ffe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276641"
---
# <a name="compiler-warning-level-1-c4129"></a>Compilateur avertissement (niveau 1) C4129
'caractère' : caractère de séquence d’échappement non reconnu  
  
 Le `character` après une barre oblique inverse (\\) dans un caractère ou une chaîne constante n’est pas reconnu comme une séquence d’échappement valide. La barre oblique inverse est ignorée et pas imprimée. Le caractère suivant la barre oblique inverse est imprimé.  
  
 Pour imprimer une barre oblique inverse unique, spécifier une double barre oblique inverse (\\\\).  
  
 La norme C++, section 2.13.2 traite des séquences d’échappement.  
  
 L’exemple suivant génère l’erreur C4129 :  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```