---
title: CRowset::MoveToRatio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- MoveToRatio
- CRowset<TAccessor>::MoveToRatio
- CRowset::MoveToRatio
- CRowset<TAccessor>.MoveToRatio
- ATL.CRowset.MoveToRatio
- ATL::CRowset::MoveToRatio
- CRowset.MoveToRatio
- ATL.CRowset<TAccessor>.MoveToRatio
- ATL::CRowset<TAccessor>::MoveToRatio
dev_langs:
- C++
helpviewer_keywords:
- MoveToRatio method
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c864933070af4f2a40572d0133027fb81f0855a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096663"
---
# <a name="crowsetmovetoratio"></a>CRowset::MoveToRatio
Extrait les lignes à partir d’une position décimale dans l’ensemble de lignes.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,bool bForward = true) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nNumerator`  
 [in] Le numérateur permet de déterminer les fractions de seconde position à partir de laquelle extraire des données.  
  
 `nDenominator`  
 [in] Le dénominateur permet de déterminer les fractions de seconde position à partir de laquelle extraire des données.  
  
 `bForward`  
 [in] Indique s’il faut déplacer vers l’avant ou vers l’arrière. La valeur par défaut est à compatibilité ascendante.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 `MoveToRatio` extrait les lignes conformément à peu près à la formule suivante :  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 Où `RowsetSize` est la taille de l’ensemble de lignes, mesurée en lignes. La précision de cette formule varie selon le fournisseur spécifique. Pour plus d’informations, consultez [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx).  
  
 Cette méthode requiert l’interface facultative `IRowsetScroll`, qui ne peut pas être pris en charge sur tous les fournisseurs ; si c’est le cas, la méthode retourne **E_NOINTERFACE**. Vous devez également définir **DBPROP_IRowsetScroll** à `VARIANT_TRUE` avant d’appeler **ouvrir** sur la table ou d’une commande qui contient l’ensemble de lignes.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRowset, classe](../../data/oledb/crowset-class.md)