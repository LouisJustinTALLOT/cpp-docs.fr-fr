---
title: Erreur du compilateur C2732 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef2faf21eb6f0c73d02ea32c7d4ed53f86eec3de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233030"
---
# <a name="compiler-error-c2732"></a>Erreur du compilateur C2732
les spécifications de la liaison contredisent les spécifications antérieures pour 'fonction'  
  
 La fonction est déjà déclarée avec un autre spécificateur de liaison.  
  
 Cette erreur peut être provoquée par des fichiers Include possédant des spécificateurs de liaison différents.  
  
 Pour corriger cette erreur, modifiez les instructions `extern` afin que les liaisons correspondent. En particulier, n'imbriquez pas de directives `#include` dans des blocs `extern "C"`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C2732 :  
  
```  
// C2732.cpp  
extern void func( void );   // implicit C++ linkage  
extern "C" void func( void );   // C2732  
```