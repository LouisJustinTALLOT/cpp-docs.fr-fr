---
title: ICommandImpl::CreateRowset | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6909f8f6825aacf55c000bfd87e0282365180559
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100640"
---
# <a name="icommandimplcreaterowset"></a>ICommandImpl::CreateRowset
Appelé par [Execute](../../data/oledb/icommandimpl-execute.md) pour créer un ensemble de lignes unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `RowsetClass`  
 Un membre de classe de modèle qui représente la classe d’ensemble de lignes de l’utilisateur. Généralement, généré par l’Assistant.  
  
 `pUnkOuter`  
 [in] Un pointeur vers le contrôle **IUnknown** si l’ensemble de lignes est créé dans le cadre d’un agrégat de l’interface ; sinon, sa valeur est null.  
  
 `riid`  
 [in] Correspond à `riid` dans `ICommand::Execute`.  
  
 `pParams`  
 [entrée/sortie] Correspond à `pParams` dans `ICommand::Execute`.  
  
 `pcRowsAffected`  
 Correspond à `pcRowsAffected` dans `ICommand::Execute`.  
  
 `ppRowset`  
 [entrée/sortie] Correspond à `ppRowset` dans `ICommand::Execute`.  
  
 `pRowsetObj`  
 [out] Pointeur vers un objet d’ensemble de lignes. En général, ce paramètre n’est pas utilisé, mais il peut être utilisé si vous devez effectuer davantage de travail sur l’ensemble de lignes avant de le transmettre à un objet COM. La durée de vie de `pRowsetObj` est liée par `ppRowset`.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard. Consultez `ICommand::Execute` pour obtenir la liste de valeurs standard.  
  
## <a name="remarks"></a>Notes  
 Pour créer plus d’un ensemble de lignes, ou pour fournir vos propres conditions de création de différents ensembles de lignes, placez les différents appels à `CreateRowset` depuis **Execute**.  
  
 Consultez [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) dans le *de référence du programmeur OLE DB.*  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [ICommandImpl, classe](../../data/oledb/icommandimpl-class.md)