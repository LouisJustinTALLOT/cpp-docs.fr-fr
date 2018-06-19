---
title: CDynamicParameterAccessor::SetParam | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
dev_langs:
- C++
helpviewer_keywords:
- SetParam method
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 37f60999eb87d473fb51bb0a493a79d0edf96074
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096637"
---
# <a name="cdynamicparameteraccessorsetparam"></a>CDynamicParameterAccessor::SetParam
Définit la mémoire tampon de paramètre en utilisant les données (autre qu’une chaîne) spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,  
               constctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  

template <class ctype>  
bool SetParam(TCHAR* pParamName,  
               const ctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ctype`  
 Un paramètre basé sur un modèle qui est le type de données.  
  
 `nParam`  
 [in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retournés. Le paramètre est l’index du paramètre en fonction de son ordre dans le SQL ou d’un appel de procédure stockée. Par exemple :  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 `pParamName`  
 [in] Le nom du paramètre.  
  
 `pData`  
 [in] Pointeur vers la mémoire contenant les données à écrire dans la mémoire tampon.  
  
 *status*  
 [in] Le `DBSTATUS` état de colonne. Pour plus d’informations sur `DBSTATUS` valeurs, consultez [état](https://msdn.microsoft.com/en-us/library/ms722617.aspx) dans les *de référence du programmeur OLE DB*, ou recherchez `DBSTATUS` dans oledb.h.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne **true** en cas de réussite ou **false** en cas d’échec.  
  
 Utilisez `SetParam` pour définir les données de paramètre de chaîne dans la mémoire tampon. Utilisez [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) pour définir les données de paramètre de chaîne dans la mémoire tampon.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)