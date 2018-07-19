---
title: Interface IRegistrar | Microsoft Docs
ms.custom: ''
ms.date: 2/1/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
dev_langs:
- C++
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6720ef830563e24d887071e1ee1e4a8c31df05c
ms.sourcegitcommit: bb4488366e4581c561ca1e573a2b99b71d4c6288
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38993566"
---
# <a name="iregistrar-interface"></a>IRegistrar, Interface
Cette interface est définie dans atliface.h et est utilisée en interne par les fonctions membres de CAtlModule notamment [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).   
  
## <a name="syntax"></a>Syntaxe  
  
```
typedef interface IRegistrar IRegistrar;
```  
## <a name="remarks"></a>Notes
Consultez la rubrique [à l’aide des paramètres remplaçables (le préprocesseur de Registrar)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) pour plus d’informations.  

## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Inscrit la ressource. |  
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Annule l’inscription de la ressource.|  
|[IRegistrar::FileRegister](#fileregister)|Enregistre le fichier.|  
|[IRegistrar::FileUnregister](#fileunregister)|Annule l’enregistrement du fichier.|  
|[IRegistrar::StringRegister](#stringregister)|Enregistre la chaîne.|  
|[IRegistrar::StringUnregister](#stringunregister)|Annule l’inscription de la chaîne|  
|[IRegistrar::ResourceRegister](#resourceregister)|Inscrit la ressource.|  
|[IRegistrar::ResourceUnregister](#resourceunregister)|Annule l’inscription de la ressource.| 
  

 
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlifase.h  
  
##  <a name="resourceregistersz"></a>  IRegistrar::ResourceRegisterSz 
 Inscrit la ressource.  
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
  
 
  
##  <a name="resourceunregistersz"></a>  IRegistrar::ResourceUnregisterSz  
 Annule l’inscription de la ressource.
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
  
  
##  <a name="fileregister"></a>  IRegistrar::FileRegister  
Enregistre le fichier.
  
```
virtual HRESULT STDMETHODCALLTYPE FileRegister( 
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
  
##  <a name="fileunregister"></a>  IRegistrar::FileUnregister  
Annule l’enregistrement du fichier.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister( 
    */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
 
##  <a name="stringregister"></a>  IRegistrar::StringRegister  
  Enregistre les données de la chaîne spécifiée.
```
virtual HRESULT STDMETHODCALLTYPE StringRegister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  
  
##  <a name="stringunregister"></a>  IRegistrar::StringUnregister
 Annule l’inscription de la chaîne de données spécifiée.  
  
```
virtualHRESULT STDMETHODCALLTYPE StringUnregister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  

  
##  <a name="resourceregister"></a>  IRegistrar::ResourceRegister  
 Inscrit la ressource.  
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
   
  
##  <a name="resourceunregister"></a>  IRegistrar::ResourceUnregister  
 Annule l’inscription de la ressource.  
  
```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0; 
```  
 
## <a name="see-also"></a>Voir aussi  
 [Utilisation de paramètres remplaçables (préprocesseur d’inscription)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Classes de module](../../atl/atl-module-classes.md)   
 [Composant de Registre (inscription)](../../atl/atl-registry-component-registrar.md)  
