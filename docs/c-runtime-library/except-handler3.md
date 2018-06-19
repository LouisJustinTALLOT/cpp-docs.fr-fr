---
title: _except_handler3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _except_handler3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _except_handler3
- except_handler3
dev_langs:
- C++
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8253db3ce5a1ec60001bb32b241bfebe000502
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389405"
---
# <a name="excepthandler3"></a>_except_handler3
Fonction CRT interne. Utilisée par une infrastructure pour rechercher le gestionnaire d'exceptions approprié pour traiter l'exception actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _except_handler3(  
   PEXCEPTION_RECORD exception_record,  
   PEXCEPTION_REGISTRATION registration,  
   PCONTEXT context,  
   PEXCEPTION_REGISTRATION dispatcher  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `exception_record`  
 Informations sur l'exception spécifique.  
  
 [in] `registration`  
 Enregistrement qui indique la table d'étendue qui doit être utilisée pour rechercher le gestionnaire d'exceptions.  
  
 [in] `context`  
 Réservé.  
  
 [in] `dispatcher`  
 Réservé.  
  
## <a name="return-value"></a>Valeur de retour  
 Si une exception doit être écartée, retourne `DISPOSITION_DISMISS`. Si l'exception doit être montée d'un niveau aux gestionnaires d'exceptions d'encapsulation, retourne `DISPOSITION_CONTINUE_SEARCH`.  
  
## <a name="remarks"></a>Notes  
 Si cette méthode trouve un gestionnaire d'exceptions approprié, l'exception est passée au gestionnaire. Dans ce cas, cette méthode ne retourne pas au code qui l'a appelée et la valeur de retour est inutile.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)