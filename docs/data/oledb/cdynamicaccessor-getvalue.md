---
title: CDynamicAccessor::GetValue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- GetValue method
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e43707d4697fbbeece5475f71b7e2f93e731772
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096416"
---
# <a name="cdynamicaccessorgetvalue"></a>CDynamicAccessor::GetValue
Récupère les données pour une colonne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
void* GetValue(DBORDINAL nColumn) const throw();  

void* GetValue(const CHAR* pColumnName) const throw();  

void* GetValue(const WCHAR* pColumnName) const throw();  

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ctype`  
 [in] Un paramètre basé sur un modèle qui gère n’importe quel type de données à l’exception des types de chaîne (**CHAR\***, **WCHAR\***), qui nécessitent un traitement particulier. `GetValue` utilise le type de données approprié en fonction de ce que vous spécifiez ici.  
  
 `nColumn`  
 [in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.  
  
 `pColumnName`  
 [in] Le nom de colonne.  
  
 `pData`  
 [out] Pointeur vers le contenu de la colonne spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 Si vous souhaitez passer des données de chaîne, utilisez les versions non de `GetValue`. Les versions non de cette méthode retournent **void\***, qui pointe vers la partie de la mémoire tampon qui contient les données de la colonne spécifiée. Retourne **NULL** si la colonne est introuvable.  
  
 Pour tous les autres types de données, il est plus simple d’utiliser les versions basées sur un modèle de `GetValue`. Les versions basées sur un modèle de retour **true** en cas de réussite ou **false** en cas d’échec.  
  
## <a name="remarks"></a>Notes  
 Utilisez les versions non pour retourner les colonnes qui contiennent des chaînes et les versions basées sur un modèle pour les colonnes qui contiennent d’autres types de données.  
  
 En mode débogage, vous obtiendrez une assertion si la taille de `pData` n’est pas égale à la taille de la colonne vers laquelle il pointe.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)