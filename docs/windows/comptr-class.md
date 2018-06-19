---
title: Comptr, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 94146661b9a00b17732ce75f75bcc0194dcbddd4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882786"
---
# <a name="comptr-class"></a>ComPtr (classe)
Crée un type de *pointeur intelligent* représentant l'interface spécifiée par le paramètre de modèle. ComPtr met à jour automatiquement un décompte de références pour le pointeur d'interface sous-jacent et libère l'interface quand le décompte de références atteint zéro.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class ComPtr;  
  
template<class T>  
friend class ComPtr;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Interface représentée par ComPtr.  
  
 `U`  
 Classe dont le ComPtr actuel est proche. (Le modèle qui utilise ce paramètre est protégé).  
  
## <a name="remarks"></a>Notes  
 ComPtr<> déclare un type qui représente le pointeur d’interface sous-jacent. Utilisez ComPtr <> pour déclarer une variable, puis utiliser l’opérateur d’accès aux membres flèche (`->`) pour accéder à une fonction membre d’interface.  
  
 Pour plus d’informations sur les pointeurs intelligents, consultez la sous-section relative aux pointeurs intelligents COM dans la rubrique [COM Coding Practices](http://msdn.microsoft.com/en-us/76aca556-b4d6-4e67-a2a3-4439900f0c39)de MSDN Library.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`InterfaceType`|Synonyme du type spécifié par le paramètre de modèle `T` .|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtr::ComPtr, constructeur](../windows/comptr-comptr-constructor.md)|Initialise une nouvelle instance de la classe ComPtr. Les surcharges fournissent des constructeurs par défaut, de copie, de déplacement et de conversion.|  
|[ComPtr::~ComPtr, destructeur](../windows/comptr-tilde-comptr-destructor.md)|Annule l’initialisation d’une instance de ComPtr.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtr::As, méthode](../windows/comptr-as-method.md)|Retourne un objet ComPtr qui représente l’interface identifiée par le paramètre de modèle spécifié.|  
|[ComPtr::AsIID, méthode](../windows/comptr-asiid-method.md)|Retourne un objet ComPtr qui représente l’interface identifiée par l’ID d’interface spécifié.|  
|[ComPtr::AsWeak, méthode](../windows/comptr-asweak-method.md)|Récupère une référence faible à l’objet actif.|  
|[ComPtr::Attach, méthode](../windows/comptr-attach-method.md)|Associe ce ComPtr au type d’interface spécifié par le paramètre de type de modèle actuel.|  
|[ComPtr::CopyTo, méthode](../windows/comptr-copyto-method.md)|Copie l’interface actuelle ou spécifiée associée à ce ComPtr au pointeur de sortie spécifié.|  
|[ComPtr::Detach, méthode](../windows/comptr-detach-method.md)|Dissocie ce ComPtr de l’interface qu’il représente.|  
|[ComPtr::Get, méthode](../windows/comptr-get-method.md)|Récupère un pointeur vers l’interface associée à ce ComPtr.|  
|[ComPtr::GetAddressOf, méthode](../windows/comptr-getaddressof-method.md)|Récupère l’adresse du membre de données [ptr_](../windows/comptr-ptr-data-member.md) qui contient un pointeur vers l’interface représentée par ce ComPtr.|  
|[ComPtr::ReleaseAndGetAddressOf, méthode](../windows/comptr-releaseandgetaddressof-method.md)|Libère l’interface associée à ce ComPtr, puis récupère l’adresse du membre de données [ptr_](../windows/comptr-ptr-data-member.md) , qui contient un pointeur vers l’interface libérée.|  
|[ComPtr::Reset](../windows/comptr-reset.md)|Libère toutes les références pour le pointeur vers l'interface qui est associée à ce ComPtr.|  
|[ComPtr::Swap, méthode](../windows/comptr-swap-method.md)|Échange l’interface gérée par le ComPtr actuel avec l’interface gérée par le ComPtr spécifié.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtr::InternalAddRef, méthode](../windows/comptr-internaladdref-method.md)|Incrémente le décompte des références de l’interface associée à ce ComPtr.|  
|[ComPtr::InternalRelease, méthode](../windows/comptr-internalrelease-method.md)|Effectue une opération de libération de COM sur l’interface associée à ce ComPtr.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType, opérateur](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|Indique si un ComPtr gère la durée de vie des objets d’une interface.|  
|[ComPtr::operator&, opérateur](../windows/comptr-operator-ampersand-operator.md)|Récupère l’adresse du ComPtr actuel.|  
|[ComPtr::operator=, opérateur](../windows/comptr-operator-assign-operator.md)|Assigne une valeur au ComPtr actuel.|  
|[ComPtr::operator->, opérateur](../windows/comptr-operator-arrow-operator.md)|Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.|  
|[ComPtr::operator==, opérateur](../windows/comptr-operator-equality-operator.md)|Indique si deux objets ComPtr sont égaux.|  
|[ComPtr::operator!=, opérateur](../windows/comptr-operator-inequality-operator.md)|Indique si deux objets ComPtr ne sont pas égaux.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[ComPtr::ptr_, données de membre](../windows/comptr-ptr-data-member.md)|Contient un pointeur vers l’interface associée à ce ComPtr, et gérée par ce dernier.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ComPtr`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)