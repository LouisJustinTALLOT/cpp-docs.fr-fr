---
title: Classe de CComDynamicUnkArray | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c3384c2c8ce03132e6525f175b9d34339b7aa26
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363921"
---
# <a name="ccomdynamicunkarray-class"></a>Classe de CComDynamicUnkArray
Cette classe stocke un tableau de **IUnknown** pointeurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComDynamicUnkArray
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Constructeur. Initialise les valeurs de la collection **NULL** et la taille de la collection à zéro.|  
|[CComDynamicUnkArray :: ~ CComDynamicUnkArray](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComDynamicUnkArray::Add](#add)|Appelez cette méthode pour ajouter un `IUnknown` pointeur vers le tableau.|  
|[CComDynamicUnkArray::begin](#begin)|Retourne un pointeur vers le premier `IUnknown` pointeur dans la collection.|  
|[CComDynamicUnkArray::clear](#clear)|Vide le tableau.|  
|[CComDynamicUnkArray::end](#end)|Retourne un pointeur vers la position au-delà de la dernière **IUnknown** pointeur dans la collection.|  
|[CComDynamicUnkArray::GetAt](#getat)|Récupère l’élément à l’index spécifié.|  
|[CComDynamicUnkArray::GetCookie](#getcookie)|Appelez cette méthode pour obtenir le cookie associé à une donnée **IUnknown** pointeur.|  
|[CComDynamicUnkArray::GetSize](#getsize)|Retourne la longueur d’un tableau.|  
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Appelez cette méthode pour obtenir le **IUnknown** pointeur associé à un cookie donné.|  
|[CComDynamicUnkArray::Remove](#remove)|Appelez cette méthode pour supprimer un **IUnknown** pointeur à partir du tableau.|  
  
## <a name="remarks"></a>Notes  
 **CComDynamicUnkArray** contient un tableau alloué dynamiquement de **IUnknown** pointeurs, chaque point d’interface sur une connexion. **CComDynamicUnkArray** peut être utilisé en tant que paramètre à la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) classe de modèle.  
  
 Le **CComDynamicUnkArray** méthodes [commencer](#begin) et [fin](#end) peut être utilisé pour parcourir tous les points de connexion (par exemple, lorsqu’un événement est déclenché).  
  
 Consultez [Ajout des Points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md) pour plus d’informations sur l’automatisation de la création d’une connexion point proxys.  
  
> [!NOTE]
> **Remarque** la classe **CComDynamicUnkArray** est utilisé par le **ajouter une classe** Assistant lors de la création d’un contrôle qui a des Points de connexion. Si vous souhaitez spécifier le nombre de Points de connexion manuellement, modifiez la référence à partir de **CComDynamicUnkArray** à `CComUnkArray<` *n* `>`, où *n*est le nombre de points de connexion requises.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="add"></a>  CComDynamicUnkArray::Add  
 Appelez cette méthode pour ajouter un **IUnknown** pointeur vers le tableau.  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 Le **IUnknown** pointeur à ajouter au tableau.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le cookie associé avec le pointeur qui vient d’être ajouté.  
  
##  <a name="begin"></a>  CComDynamicUnkArray::begin  
 Retourne un pointeur vers le début de la collection de **IUnknown** des pointeurs d’interface.  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un **IUnknown** pointeur d’interface.  
  
### <a name="remarks"></a>Notes  
 La collection contient des pointeurs aux interfaces stockées localement en tant que **IUnknown**. Vous effectuez un cast **IUnknown** de l’interface pour le type d’interface réelle, puis appelez par son biais. Vous n’avez pas besoin interroger tout d’abord pour l’interface.  
  
 Avant d’utiliser le **IUnknown** interface, vous devez vérifier qu’il n’est pas **NULL**.  
  
##  <a name="clear"></a>  CComDynamicUnkArray::clear  
 Vide le tableau.  
  
```
void clear();
```  
  
##  <a name="ccomdynamicunkarray"></a>  CComDynamicUnkArray::CComDynamicUnkArray  
 Constructeur.  
  
```
CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>Notes  
 Définit la taille de la collection à zéro et initialise les valeurs à **NULL**. Le destructeur libère de la collection, si nécessaire.  
  
##  <a name="dtor"></a>  CComDynamicUnkArray :: ~ CComDynamicUnkArray  
 Destructeur.  
  
```
~CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>Notes  
 Libère les ressources allouées par le constructeur de classe.  
  
##  <a name="end"></a>  CComDynamicUnkArray::end  
 Retourne un pointeur vers la position au-delà de la dernière **IUnknown** pointeur dans la collection.  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un **IUnknown** pointeur d’interface.  
  
##  <a name="getat"></a>  CComDynamicUnkArray::GetAt  
 Récupère l’élément à l’index spécifié.  
  
```
IUnknown* GetAt(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de l'élément à récupérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interface.  
  
##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie  
 Appelez cette méthode pour obtenir le cookie associé à une donnée **IUnknown** pointeur.  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>Paramètres  
 `ppFind`  
 Le **IUnknown** pointeur pour laquelle le cookie associé est requis.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le cookie associé à la **IUnknown** pointeur, ou zéro si aucune correspondance **IUnknown** pointeur est trouvé.  
  
### <a name="remarks"></a>Notes  
 S’il existe plus d’une instance du même **IUnknown** pointeur, cette fonction retourne le cookie pour le.  
  
##  <a name="getsize"></a>  CComDynamicUnkArray::GetSize  
 Retourne la longueur d’un tableau.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Longueur du tableau.  
  
##  <a name="getunknown"></a>  CComDynamicUnkArray::GetUnknown  
 Appelez cette méthode pour obtenir le **IUnknown** pointeur associé à un cookie donné.  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 Le cookie pour lequel associé **IUnknown** pointeur est requis.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le **IUnknown** pointeur, ou NULL si aucun cookie correspondant est trouvé.  
  
##  <a name="remove"></a>  CComDynamicUnkArray::Remove  
 Appelez cette méthode pour supprimer un **IUnknown** pointeur à partir du tableau.  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 Le référencement de cookie la **IUnknown** pointeur à supprimer du tableau.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE si le pointeur est supprimé ; Sinon, FALSE.  
  
## <a name="see-also"></a>Voir aussi  
 [CComUnkArray (classe)](../../atl/reference/ccomunkarray-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
