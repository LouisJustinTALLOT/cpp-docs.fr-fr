---
title: CRowsetImpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- CRowsetImpl class
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eece641adacd6ce918929366c4fc6dc78105e71a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098717"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl, classe
Fournit une implémentation d’ensemble de lignes OLE DB standard sans nécessiter l’héritage multiple de nombreuses interfaces d’implémentation.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,  
   class Storage,  
   class CreatorClass,  
   class ArrayType = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class RowsetInterface = IRowsetImpl <T, IRowset>   
>  
class CRowsetImpl :    
   public CComObjectRootEx<CreatorClass::_ThreadModel>,   
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,   
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Classe de l’utilisateur qui dérive de `CRowsetImpl`.  
  
 `Storage`  
 La classe d’enregistrement utilisateur.  
  
 `CreatorClass`  
 La classe qui contient les propriétés de l’ensemble de lignes ; en général, la commande.  
  
 `ArrayType`  
 La classe qui agira en tant que stockage pour les données de l’ensemble de lignes. Ce paramètre par défaut est `CAtlArray`, mais il peut être n’importe quelle classe qui prend en charge la fonctionnalité requise.  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|Extrait une chaîne à partir d’un **DBID** et la copie à le `bstr` passé.|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|Valide et stocke le **DBID**s dans les deux chaînes ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|  
  
### <a name="overridable-methods"></a>Méthodes substituables  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/crowsetimpl-getcolumninfo.md)|Récupère les informations de colonne pour une demande de client particulier.|  
|[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)|Vérifie si un ou les deux paramètres contiennent des valeurs de chaîne et dans ce cas, copie les valeurs de chaîne dans les données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
|[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)|Une vérification pour voir si un ou les deux **DBID**s contiennent des valeurs de chaîne et dans ce cas, les copie dans ses données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|Par défaut, un `CAtlArray` qui templatizes sur l’argument de modèle d’enregistrement utilisateur `CRowsetImpl`. Une autre classe de type tableau peut être utilisée en modifiant le `ArrayType` d’argument template pour `CRowsetImpl`.|  
|[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|Contient la commande initiale de l’ensemble de lignes.|  
|[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|Contient l’index de départ de l’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 `CRowsetImpl` Fournit des remplacements dans le formulaire d’effectue un upcast statique. Les méthodes de contrôlent la manière dans lequel un ensemble de lignes donné validera le texte de la commande. Vous pouvez créer vos propres `CRowsetImpl`-classe de style en effectuant vos interfaces de l’implémentation héritée de multiples. La seule méthode pour laquelle vous devez fournir l’implémentation est **Execute**. Selon le type de l’ensemble de lignes que vous créez, les méthodes creator seront attend à recevoir des signatures différentes pour **Execute**. Par exemple, si vous utilisez un `CRowsetImpl`-dérivée de la classe pour implémenter un ensemble de lignes de schéma, le **Execute** méthode aura la signature suivante :  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 Si vous créez un `CRowsetImpl`-dérivée de la classe pour implémenter une commande ou un ensemble de lignes de la session, le **Execute** méthode aura la signature suivante :  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 Pour mettre en œuvre toutes la `CRowsetImpl`-dérivée **Execute** méthodes, vous devez remplir vos tampons de données interne ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h