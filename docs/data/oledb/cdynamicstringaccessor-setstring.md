---
title: CDynamicStringAccessor::SetString | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method
ms.assetid: 94846d8b-4c1b-47fe-acdc-1752981cee25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5f4b7f9354de7f6c6ad10ba472bfd31873a0355
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095903"
---
# <a name="cdynamicstringaccessorsetstring"></a>CDynamicStringAccessor::SetString
Définit les données de la colonne spécifiée sous forme de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT SetString(DBORDINAL nColumn,  
  BaseType* data) throw();  


HRESULT SetString(const CHAR* pColumnName,  
   BaseType* data) throw();  


HRESULT SetString(const WCHAR* pColumnName,  
   BaseType* data) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nColumn`  
 [in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur spéciale 0 fait référence à la colonne de signet, le cas échéant.  
  
 `pColumnName`  
 [in] Pointeur vers une chaîne de caractères qui contient le nom de colonne.  
  
 `data`  
 [in] Pointeur vers les données de chaîne à écrire dans la colonne spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur vers la valeur de chaîne pour lequel définir la colonne spécifiée. La valeur est de type `BaseType`, qui sera `CHAR` ou `WCHAR` selon que `_UNICODE` est défini ou non.  
  
## <a name="remarks"></a>Notes  
 La seconde substituer formulaire prend le nom de colonne sous forme de chaîne ANSI ainsi le troisième formulaire prend le nom de colonne sous forme de chaîne Unicode.  
  
 Si `_SECURE_ATL` est défini pour avoir une valeur différente de zéro, un échec d’assertion runtime sera généré si l’entrée `data` chaîne est plus longue que la longueur maximale autorisée de la colonne de données référencée. Sinon, la chaîne d’entrée sera être tronquée si elle est supérieure à la longueur maximale autorisée.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicStringAccessor, classe](../../data/oledb/cdynamicstringaccessor-class.md)