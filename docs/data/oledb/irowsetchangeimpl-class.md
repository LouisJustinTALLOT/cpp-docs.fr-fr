---
title: Classe IRowsetChangeImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 11435cd1372147efb14aed78448d889fd60dc5a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106039"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl Class
L’implémentation de modèles OLE DB de la [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) interface dans la spécification OLE DB.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Une classe dérivée de `IRowsetChangeImpl`.  
  
 `Storage`  
 L’enregistrement d’utilisateur.  
  
 `BaseInterface`  
 La classe de base pour l’interface, tel que `IRowsetChange`.  
  
 `RowClass`  
 L’unité de stockage pour le descripteur de ligne.  
  
 `MapClass`  
 L’unité de stockage pour tous les descripteurs de ligne détenus par le fournisseur.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Méthodes d’interface (utilisés avec IRowsetChange)  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|Supprime les lignes à partir de l’ensemble de lignes.|  
|[insertRow](../../data/oledb/irowsetchangeimpl-insertrow.md)|Insère une ligne dans l’ensemble de lignes.|  
|[SetData](../../data/oledb/irowsetchangeimpl-setdata.md)|Définit les valeurs de données dans une ou plusieurs colonnes.|  
  
### <a name="implementation-method-callback"></a>Méthode d’implémentation (rappel)  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|Substitué par le fournisseur pour valider les données dans son magasin.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est responsable des opérations d’écriture immédiate dans un magasin de données. « Exécution » signifie que lorsque l’utilisateur final (la personne à l’aide du consommateur) effectue des modifications, ces modifications sont immédiatement transmises aux données stocker (et ne peut pas être annulée).  
  
 `IRowsetChangeImpl` implémente le OLE DB `IRowsetChange` interface, ce qui permet la mise à jour des valeurs des colonnes dans les lignes existantes, la suppression de lignes et l’insertion de nouvelles lignes.  
  
 L’implémentation des modèles OLE DB prend en charge toutes les méthodes de base (`SetData`, `InsertRow`, et `DeleteRows`).  
  
> [!IMPORTANT]
>  Il est fortement recommandé de lire la documentation suivante avant de tenter d’implémenter votre fournisseur :  
  
-   [Création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Chapitre 6 de la *de référence du programmeur OLE DB*  
  
-   Consultez également la `RUpdateRowset` classe est utilisée dans l’exemple UpdatePV  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)