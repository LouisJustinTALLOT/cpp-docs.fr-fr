---
title: Classe IPersistStreamInitImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a51dd5e198a86b7bb17a6182c1edb098f23a8e47
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360454"
---
# <a name="ipersiststreaminitimpl-class"></a>Classe IPersistStreamInitImpl
Cette classe implémente **IUnknown** et fournit une implémentation par défaut de la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interface.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IPersistStreamInitImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Récupère la taille du flux requis pour enregistrer les données de l’objet. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IPersistStreamInitImpl::InitNew](#initnew)|Initialise un objet nouvellement créé.|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Vérifie si les données de l’objet a changé depuis son dernier enregistrement.|  
|[IPersistStreamInitImpl::Load](#load)|Charge les propriétés de l’objet à partir du flux spécifié.|  
|[IPersistStreamInitImpl::Save](#save)|Enregistre les propriétés de l’objet dans le flux spécifié.|  
  
## <a name="remarks"></a>Notes  
 Le [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interface permet à un client de demander que votre objet de charge et enregistre ses données persistantes dans un flux unique. Classe `IPersistStreamInitImpl` fournit une implémentation par défaut de cette interface et implémente **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID  
 Récupère le CLSID de l’objet.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) dans le Kit de développement logiciel Windows.  
  
##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax  
 Récupère la taille du flux requis pour enregistrer les données de l’objet.  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287) dans le Kit de développement logiciel Windows.  
  
##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew  
 Initialise un objet nouvellement créé.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234) dans le Kit de développement logiciel Windows.  
  
##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty  
 Vérifie si les données de l’objet a changé depuis son dernier enregistrement.  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092) dans le Kit de développement logiciel Windows.  
  
##  <a name="load"></a>  IPersistStreamInitImpl::Load  
 Charge les propriétés de l’objet à partir du flux spécifié.  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>Notes  
 ATL utilise le mappage des propriétés de l’objet pour récupérer ces informations.  
  
 Consultez [IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730) dans le Kit de développement logiciel Windows.  
  
##  <a name="save"></a>  IPersistStreamInitImpl::Save  
 Enregistre les propriétés de l’objet dans le flux spécifié.  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>Notes  
 ATL utilise le mappage des propriétés de l’objet pour stocker ces informations.  
  
 Consultez [IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux et stockages](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
