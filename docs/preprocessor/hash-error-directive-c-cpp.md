---
title: '#erreur Directive (C/C++) | Documents Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#error'
dev_langs: C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a14786834843046fc1e6cf551eaf95d1b28a8624
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="error-directive-cc"></a>#error, directive (C/C++)
Le `#error` directive émet un message d’erreur spécifié par l’utilisateur au moment de la compilation, puis se termine la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Notes  
 Cette directive émet le message d’erreur inclut le *chaîne de jeton* paramètre. Le `token-string` paramètre n’est pas soumis à une expansion de macro. Cette directive est très utile lors du prétraitement pour informer le développeur d’une incohérence de programme ou de la violation d’une contrainte. L’exemple suivant illustre l’erreur lors du traitement lors du prétraitement :  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives de préprocesseur](../preprocessor/preprocessor-directives.md)