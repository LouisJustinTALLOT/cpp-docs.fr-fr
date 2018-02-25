---
title: IDBSchemaRowsetImpl::CheckRestrictions | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
dev_langs:
- C++
helpviewer_keywords:
- CheckRestrictions method
ms.assetid: 3c9d77d2-0e4b-48fa-80db-d735da19f1cf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 44e661bc782af4a162936caae7c8c1be06585647
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="idbschemarowsetimplcheckrestrictions"></a>IDBSchemaRowsetImpl::CheckRestrictions
Vérifie la validité des restrictions par rapport à un ensemble de lignes de schéma.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT CheckRestrictions(REFGUID rguidSchema,  
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rguidSchema`  
 [in] Référence au GUID d’ensemble de lignes de schéma demandé (par exemple, `DBSCHEMA_TABLES`).  
  
 `cRestrictions`  
 [in] Nombre de restrictions passées par le consommateur pour l’ensemble de lignes de schéma.  
  
 `rgRestrictions`  
 [in] Tableau de longueur *cRestrictions* des valeurs de restriction à définir. Pour plus d'informations, consultez la description du paramètre `rgRestrictions` de [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode `CheckRestrictions` pour vérifier la validité des restrictions par rapport à un ensemble de lignes de schéma. Elle vérifie les restrictions pour les ensembles de lignes de schéma `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**et **DBSCHEMA_PROVIDER_TYPES** . Appelez-la pour déterminer si l’appel d’un consommateur à **IDBSchemaRowset::GetRowset** est correct. Si vous voulez prendre en charge d’autres ensembles de lignes de schéma que ceux répertoriés ci-dessus, vous devez créer votre propre fonction pour mener à bien cette tâche.  
  
 `CheckRestrictions` détermine si le consommateur appelle [GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) avec la restriction et le type de restriction appropriés (par exemple, un `VT_BSTR` pour une chaîne) que le fournisseur prend en charge. De même, elle détermine si le nombre correct de restrictions est pris en charge. Par défaut, `CheckRestrictions` demande au fournisseur, via l’appel [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) , quelles restrictions il prend en charge dans un ensemble de lignes donné. La méthode compare ensuite les restrictions du consommateur à celles que prend en charge le fournisseur avant d’aboutir ou d’échouer.  
  
 Pour plus d’informations sur les ensembles de lignes de schéma, consultez [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) dans les *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IDBSchemaRowsetImpl Class](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Membres IDBSchemaRowsetImpl (classe)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)