---
title: Module::registercomobject, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c997b4221dee913a6eaad55f6f114b0ad9d820e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606538"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject, méthode
Inscrit un ou plusieurs objets COM afin d’autres applications peuvent se connecter à leur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
### <a name="parameters"></a>Paramètres  
 *Nom du serveur*  
 Nom qualifié complet d’un serveur.  
  
 *CLSID*  
 Tableau de CLSID à inscrire.  
  
 *fabriques*  
 Tableau d’interfaces IUnknown des objets de classe dont la disponibilité est en cours de publication.  
  
 *Cookies*  
 Lorsque l’opération se termine, un tableau de pointeurs vers des valeurs qui identifient la classe des objets qui ont été enregistrés. Ces valeurs sont utilisées ultérieurement révoque l’inscription.  
  
 *count*  
 Le nombre de CLSID à inscrire.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si réussies ; Sinon, un HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.  
  
## <a name="remarks"></a>Notes  
 Les objets COM sont enregistrés avec l’énumérateur CLSCTX_LOCAL_SERVER de l’énumération CLSCTX.  
  
 Le type de connexion pour les objets inscrits est spécifié par une combinaison de cours *comflag* paramètre de modèle et de l’énumérateur REGCLS_SUSPENDED de l’énumération REGCLS.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)