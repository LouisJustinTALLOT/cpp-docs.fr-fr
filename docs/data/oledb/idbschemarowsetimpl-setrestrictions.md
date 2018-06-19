---
title: IDBSchemaRowsetImpl::SetRestrictions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
dev_langs:
- C++
helpviewer_keywords:
- SetRestrictions method
ms.assetid: 707d5065-b853-4d38-9b67-3066b4d3b279
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b6effd432b033941d404c4935cdbad5a2336ac8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105853"
---
# <a name="idbschemarowsetimplsetrestrictions"></a>IDBSchemaRowsetImpl::SetRestrictions
Spécifie les restrictions que vous prenez en charge sur un ensemble de lignes de schéma particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```
void SetRestrictions(ULONG cRestrictions,  
  GUID* /* rguidSchema */,  
   ULONG* rgRestrictions);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cRestrictions`  
 [in] Nombre de restrictions présentes dans le tableau `rgRestrictions` et nombre de GUID figurant dans le tableau `rguidSchema` .  
  
 `rguidSchema`  
 [in] Tableau des GUID des ensembles de lignes de schéma pour lesquels les restrictions doivent être récupérées. Chaque élément de tableau contient le GUID d’un ensemble de lignes de schéma (par exemple, `DBSCHEMA_TABLES`).  
  
 `rgRestrictions`  
 [in] Tableau de longueur `cRestrictions` des valeurs de restriction à définir. Chaque élément correspond aux restrictions de l’ensemble de lignes de schéma identifié par le GUID. Si un ensemble de lignes de schéma n’est pas pris en charge par le fournisseur, la valeur définie de l’élément est zéro. Dans le cas contraire, la valeur **ULONG** contient un masque de bits qui représente les restrictions prises en charge sur cet ensemble de lignes de schéma. Pour plus d’informations sur les restrictions correspondant à un ensemble de lignes de schéma particulier, consultez la table de l’ensemble de lignes de schéma GUID dans [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) dans les *de référence du programmeur OLE DB* dans les fenêtres KIT DE DÉVELOPPEMENT LOGICIEL.  
  
## <a name="remarks"></a>Notes  
 L’objet **IDBSchemaRowset** appelle la méthode `SetRestrictions` pour identifier les restrictions que vous prenez en charge sur un ensemble de lignes de schéma déterminé (elle est appelée par [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) via un pointeur converti en supertype). Les restrictions permettent aux consommateurs de récupérer uniquement les lignes correspondantes (par exemple, toutes les colonnes de la table « MaTable »). Les restrictions sont facultatives, et dans le cas où aucune n’est prise en charge (par défaut), toutes les données sont systématiquement retournées.  
  
 L’implémentation par défaut de cette méthode attribue aux éléments de tableau `rgRestrictions` la valeur 0. Remplacez la valeur par défaut dans votre classe session pour définir d’autres restrictions que celle par défaut.  
  
 Pour plus d’informations sur l’implémentation de la prise en charge des ensembles de lignes de schéma, consultez [Prise en charge des ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md).  
  
 Pour obtenir un exemple de fournisseur qui prend en charge les ensembles de lignes de schéma, consultez l’exemple [UpdatePV](../../visual-cpp-samples.md) .  
  
 Pour plus d’informations sur les ensembles de lignes de schéma, consultez [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) dans les *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IDBSchemaRowsetImpl (classe)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Membres IDBSchemaRowsetImpl (classe)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Classes d’ensemble de lignes de schéma et Classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [Prise en charge des ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md)   
 [UpdatePV](../../visual-cpp-samples.md)