---
title: CDynamicAccessor::SetValue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- SetValue method
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9322394f2b72b49afe988c371858d9ee580825ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095675"
---
# <a name="cdynamicaccessorsetvalue"></a>CDynamicAccessor::SetValue
Stocke les données d’une colonne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <class ctype>
bool SetValue(   
   DBORDINAL nColumn,   
   constctype& data) throw( );  

template <class ctype>    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data) throw( );  

template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data) throw( );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ctype`  
 [in] Un paramètre basé sur un modèle qui gère n’importe quel type de données à l’exception des types de chaîne (**CHAR\***, **WCHAR\***), qui nécessitent un traitement particulier. `GetValue` utilise le type de données approprié en fonction de ce que vous spécifiez ici.  
  
 `pColumnName`  
 [in] Pointeur vers une chaîne de caractères contenant le nom de colonne.  
  
 `data`  
 [in] Pointeur vers la mémoire contenant les données.  
  
 `nColumn`  
 [in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.  
  
## <a name="return-value"></a>Valeur de retour  
 Si vous souhaitez définir les données de chaîne, utilisez les versions non de `GetValue`. Les versions non de cette méthode retournent **void\***, qui pointe vers la partie de la mémoire tampon qui contient les données de la colonne spécifiée. Retourne **NULL** si la colonne est introuvable.  
  
 Pour tous les autres types de données, il est plus simple d’utiliser les versions basées sur un modèle de `GetValue`. Les versions basées sur un modèle de retour **true** en cas de réussite ou **false** en cas d’échec.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)