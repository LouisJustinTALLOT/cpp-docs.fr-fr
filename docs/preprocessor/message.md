---
title: message | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message_CPP
- vc-pragma.message
dev_langs: C++
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b62961ebd1327e8f8a844482b1490b21b4e9c34
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="message"></a>message
Envoie un littéral de chaîne à la sortie standard sans mettre fin à la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma message( messagestring )  
```  
  
## <a name="remarks"></a>Remarques  
 En règle générale le **message** pragma consiste à afficher des messages d’information au moment de la compilation.  
  
 Le *messagestring* paramètre peut être une macro qui se développe en un littéral de chaîne, et vous pouvez concaténer ces macros avec des littéraux de chaîne de n’importe quelle combinaison.  
  
 Si vous utilisez une macro prédéfinie dans le **message** pragma, la macro doit retourner une chaîne, sans quoi vous devez convertir la sortie de la macro en chaîne.  
  
 Le fragment de code suivant utilise la **message** pragma pour afficher des messages lors de la compilation :  
  
```  
// pragma_directives_message1.cpp  
// compile with: /LD  
#if _M_IX86 >= 500  
#pragma message("_M_IX86 >= 500")  
#endif  
  
#pragma message("")  
  
#pragma message( "Compiling " __FILE__ )   
#pragma message( "Last modified on " __TIMESTAMP__ )  
  
#pragma message("")  
  
// with line number  
#define STRING2(x) #x  
#define STRING(x) STRING2(x)  
  
#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")  
  
#pragma message("")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)