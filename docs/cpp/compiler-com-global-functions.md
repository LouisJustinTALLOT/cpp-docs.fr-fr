---
title: Fonctions globales COM du compilateur | Microsoft Docs
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
ms.openlocfilehash: aa138b045fcb5851a65b68d898b99a8cab269f6e
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402531"
---
# <a name="compiler-com-global-functions"></a>Fonctions globales COM du compilateur
**Section spécifique à Microsoft**  
  
 Les routines suivantes sont disponibles :  
  
|Fonction|Description|  
|--------------|-----------------|  
|[_com_raise_error](../cpp/com-raise-error.md)|Lève une [_com_error](../cpp/com-error-class.md) en réponse à une défaillance.|  
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Remplace la fonction par défaut utilisée pour la gestion des erreurs COM.|  
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convertit un `BSTR` valeur à un `char *`.|  
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convertit un `char *` valeur à un `BSTR`.|  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)   
 [Prise en charge COM du compilateur](../cpp/compiler-com-support.md)