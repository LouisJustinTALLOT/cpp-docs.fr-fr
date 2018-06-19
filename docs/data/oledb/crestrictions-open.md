---
title: CRestrictions::Open | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8039d55312687cc28be27f2ed7726b9bda1b44aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097430"
---
# <a name="crestrictionsopen"></a>CRestrictions::Open
Retourne un résultat défini selon les restrictions fournies par l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `session`  
 [in] Spécifie un objet de session existant utilisé pour se connecter à la source de données.  
  
 *lpszParam*  
 [in] Spécifie les restrictions sur l’ensemble de lignes de schéma.  
  
 `bBind`  
 [in] Spécifie s’il faut lier automatiquement de mapper les colonnes. La valeur par défaut est **true**, ce qui entraîne le mappage de colonnes à lier automatiquement. Paramètre `bBind` à **false** empêche la liaison automatique de la carte de la colonne afin que vous pouvez lier manuellement. (Liaison manuelle est particulièrement intéressant pour les utilisateurs OLAP).  
  
## <a name="return-value"></a>Valeur de retour  
 Un de la norme `HRESULT` valeurs.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier un maximum de sept restrictions sur un ensemble de lignes de schéma.  
  
 Consultez [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) pour plus d’informations sur les restrictions définies sur chaque ensemble de lignes de schéma.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbsch.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRestrictions, classe](../../data/oledb/crestrictions-class.md)   
 [Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)