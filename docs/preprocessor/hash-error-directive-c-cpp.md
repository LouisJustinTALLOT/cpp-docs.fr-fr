---
title: '#erreur Directive (C/C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#error'
dev_langs:
- C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2da939fe52e41e122ecd4926e34fb9c4be735ae
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539180"
---
# <a name="error-directive-cc"></a>#error, directive (C/C++)
Le **#error** directive émet un message d’erreur spécifié par l’utilisateur au moment de la compilation, puis termine la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Notes  
 
Le message d’erreur qui émet cette directive inclut le *chaîne de jeton* paramètre. Le *chaîne de jeton* paramètre n’est pas soumis à une expansion macro. Cette directive est particulièrement utile pendant le prétraitement pour notifier le développeur d’une incohérence de programme ou de la violation d’une contrainte. L’exemple suivant illustre l’erreur lors du traitement pendant le prétraitement :  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>Voir aussi  
 
[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)