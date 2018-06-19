---
title: Les fonctions globales COM du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4116d82ef38d7aaab29fe682e0881ac2e2ff5903
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412187"
---
# <a name="compiler-com-global-functions"></a>Fonctions globales COM du compilateur
**Section spécifique à Microsoft**  
  
 Les routines suivantes sont disponibles :  
  
|Fonction|Description|  
|--------------|-----------------|  
|[_com_raise_error](../cpp/com-raise-error.md)|Lève un [_com_error](../cpp/com-error-class.md) en réponse à un échec.|  
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Remplace la fonction par défaut utilisée pour la gestion des erreurs COM.|  
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convertit un `BSTR` valeur un **char \*** .|  
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convertit un **char \***  la valeur en un `BSTR`.|  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)   
 [Prise en charge COM du compilateur](../cpp/compiler-com-support.md)