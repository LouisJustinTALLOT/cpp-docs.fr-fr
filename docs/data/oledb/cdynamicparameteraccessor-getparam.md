---
title: CDynamicParameterAccessor::GetParam | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
dev_langs:
- C++
helpviewer_keywords:
- GetParam method
ms.assetid: 893a6bf8-7b55-4f6d-8a10-a43b13be7f56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3596cf8fc445a5607c008be687c44cafb713049b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090899"
---
# <a name="cdynamicparameteraccessorgetparam"></a>CDynamicParameterAccessor::GetParam
Récupère les données de chaîne pour un paramètre spécifique à partir de la mémoire tampon de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,   
  ctype* pData) const throw();  

template <class ctype> bool GetParam(TCHAR* pParamName,   
   ctype* pData) const throw();  

void* GetParam(DBORDINAL nParam) const throw();  

void* GetParam(TCHAR* pParamName) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ctype`  
 Un paramètre basé sur un modèle qui est le type de données.  
  
 `nParam`  
 [in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retournés. Le paramètre est l’index du paramètre en fonction de son ordre dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.  
  
 `pParamName`  
 [in] Le nom du paramètre.  
  
 `pData`  
 [out] Pointeur vers la mémoire contenant les données extraites de la mémoire tampon.  
  
## <a name="return-value"></a>Valeur de retour  
 Pour les versions non, pointe vers la mémoire contenant les données récupérées à partir de la mémoire tampon. Pour les versions basées sur un modèle, retourne **true** en cas de réussite ou **false** en cas d’échec.  
  
 Utilisez `GetParam` pour récupérer des données de paramètre de chaîne à partir de la mémoire tampon. Utilisez [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) pour récupérer les données de paramètre de chaîne à partir de la mémoire tampon.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)