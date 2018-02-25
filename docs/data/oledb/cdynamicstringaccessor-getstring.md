---
title: CDynamicStringAccessor::GetString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
dev_langs:
- C++
helpviewer_keywords:
- GetString method
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c6a2340ddd0e123720cd59bb2ee0bf8ca58504f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicstringaccessorgetstring"></a>CDynamicStringAccessor::GetString
Récupère les données de la colonne spécifiée sous forme de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nColumn`  
 [in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.  
  
 `pColumnName`  
 [in] Pointeur vers une chaîne de caractères qui contient le nom de colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la valeur de chaîne sont extraites de la colonne spécifiée. La valeur est de type ***BaseType***, qui sera **CHAR** ou **WCHAR** selon si _UNICODE est défini ou non. Retourne NULL si la colonne spécifiée est introuvable.  
  
## <a name="remarks"></a>Notes  
 La seconde remplacer formulaire prend le nom de colonne sous forme de chaîne ANSI. La troisième remplacer formulaire prend le nom de colonne sous forme de chaîne Unicode.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicStringAccessor, classe](../../data/oledb/cdynamicstringaccessor-class.md)