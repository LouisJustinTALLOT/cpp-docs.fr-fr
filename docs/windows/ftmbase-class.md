---
title: Ftmbase, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
dev_langs:
- C++
helpviewer_keywords:
- FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed3e9b9e66f673a3d86ded7b3d576e1203db9595
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570559"
---
# <a name="ftmbase-class"></a>FtmBase (classe)
Représente un objet marshaler libre de threads.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,   
   Microsoft::WRL::CloakedIid<IMarshal> >;  
```  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [runtimeclass, classe](runtimeclass-class.md).  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[FtmBase::FtmBase, constructeur](../windows/ftmbase-ftmbase-constructor.md)|Initialise une nouvelle instance de la **FtmBase** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable, méthode](../windows/ftmbase-createglobalinterfacetable-method.md)|Crée un tableau global d’interface (GIT).|  
|[FtmBase::DisconnectObject, méthode](../windows/ftmbase-disconnectobject-method.md)|Force libère toutes les connexions externes à un objet. Serveur de l’objet appelle l’implémentation de l’objet de cette méthode avant d’arrêter.|  
|[FtmBase::GetMarshalSizeMax, méthode](../windows/ftmbase-getmarshalsizemax-method.md)|Obtenir la limite supérieure sur le nombre d’octets nécessaires pour marshaler le pointeur d’interface spécifié sur l’objet spécifié.|  
|[FtmBase::GetUnmarshalClass, méthode](../windows/ftmbase-getunmarshalclass-method.md)|Obtient le CLSID COM utilise pour localiser la DLL contenant le code pour le proxy correspondant. COM charge cette DLL pour créer une instance non initialisée du proxy.|  
|[FtmBase::MarshalInterface, méthode](../windows/ftmbase-marshalinterface-method.md)|Écrit dans un flux les données requises pour initialiser l’objet proxy dans un processus client.|  
|[FtmBase::ReleaseMarshalData, méthode](../windows/ftmbase-releasemarshaldata-method.md)|Détruit un paquet de données marshalé.|  
|[FtmBase::UnmarshalInterface, méthode](../windows/ftmbase-unmarshalinterface-method.md)|Initialise un proxy nouvellement créé et retourne un pointeur d’interface au proxy.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[FtmBase::marshaller_, données de membre](../windows/ftmbase-marshaller-data-member.md)|Contient une référence à FTM.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `FtmBase`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)