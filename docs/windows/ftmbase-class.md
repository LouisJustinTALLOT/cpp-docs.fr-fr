---
title: Ftmbase, classe | Documents Microsoft
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
ms.openlocfilehash: 38f30c497fc8640b1f88f4ffb3fc6f14bed55a3e
ms.sourcegitcommit: e3b4ef19b534a2ed48bb9091e5197a6e536f16c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814350"
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
|[FtmBase::FtmBase, constructeur](../windows/ftmbase-ftmbase-constructor.md)|Initialise une nouvelle instance de la classe FtmBase.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable, méthode](../windows/ftmbase-createglobalinterfacetable-method.md)|Crée un tableau global d’interface (GIT).|  
|[FtmBase::DisconnectObject, méthode](../windows/ftmbase-disconnectobject-method.md)|Force libère toutes les connexions externes à un objet. Serveur de l’objet appelle l’implémentation de l’objet de cette méthode avant d’arrêter.|  
|[FtmBase::GetMarshalSizeMax, méthode](../windows/ftmbase-getmarshalsizemax-method.md)|Obtenir la limite supérieure du nombre d’octets nécessaire pour marshaler le pointeur d’interface spécifié sur l’objet spécifié.|  
|[FtmBase::GetUnmarshalClass, méthode](../windows/ftmbase-getunmarshalclass-method.md)|Obtient le CLSID COM utilise pour rechercher la DLL qui contient le code pour le proxy correspondant. COM charge cette DLL pour créer une instance non initialisée du proxy.|  
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