---
title: Module::registercomobject, méthode | Documents Microsoft
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
ms.openlocfilehash: c002dd64049006c8ee74c709c585a3a9d0f253a5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873977"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject, méthode
Inscrit un ou plusieurs objets COM pour d’autres applications peuvent s’y connecter.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `serverName`  
 Nom qualifié complet d’un serveur.  
  
 `clsids`  
 Tableau de CLSID à inscrire.  
  
 `factories`  
 Tableau d’interfaces IUnknown des objets de classe dont la disponibilité est en cours de publication.  
  
 `cookies`  
 Lorsque l’opération est terminée, un tableau de pointeurs vers les valeurs qui identifient la classe d’objets qui ont été enregistrés. Ces valeurs sont utilisées ultérieurement Annuler l’inscription.  
  
 `count`  
 Le nombre de CLSID à inscrire.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si successfu ; Sinon, un HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.  
  
## <a name="remarks"></a>Notes  
 Les objets COM sont enregistrés avec l’énumérateur CLSCTX_LOCAL_SERVER de l’énumération CLSCTX.  
  
 Le type de connexion pour les objets inscrits est spécifié par une combinaison d’actuel `comflag` paramètre de modèle et de l’énumérateur REGCLS_SUSPENDED de l’énumération REGCLS.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)