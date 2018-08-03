---
title: ComPtr, classe | Microsoft Docs
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
ms.openlocfilehash: 21503e38bb612f935e26f6eaaa93df2097e10445
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465335"
---
# <a name="comptr-class"></a>ComPtr (classe)
Crée un type de *pointeur intelligent* représentant l'interface spécifiée par le paramètre de modèle. **ComPtr** automatiquement conserve un décompte de références pour le pointeur d’interface sous-jacent et libère l’interface lorsque le décompte de références atteint zéro.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class ComPtr;  
  
template<class T>  
friend class ComPtr;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 L’interface qui le **ComPtr** représente.  
  
 *U*  
 Une classe à laquelle actuel **ComPtr** soit un assembly friend. (Le modèle qui utilise ce paramètre est protégé).  
  
## <a name="remarks"></a>Notes  
 `ComPtr<>` déclare un type qui représente le pointeur d’interface sous-jacent. Utilisez `ComPtr<>` pour déclarer une variable, puis utiliser l’opérateur member-access flèche (`->`) pour accéder à une fonction membre d’interface.  
  
 Pour plus d’informations sur les pointeurs intelligents, consultez la sous-section « Pointeurs intelligents COM » le [COM Coding Practices](http://msdn.microsoft.com/76aca556-b4d6-4e67-a2a3-4439900f0c39)rubrique dans MSDN Library.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`InterfaceType`|Un synonyme du type spécifié par le *T* paramètre de modèle.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtr::ComPtr, constructeur](../windows/comptr-comptr-constructor.md)|Initialise une nouvelle instance de la **ComPtr** classe. Les surcharges fournissent des constructeurs par défaut, de copie, de déplacement et de conversion.|  
|[ComPtr::~ComPtr, destructeur](../windows/comptr-tilde-comptr-destructor.md)|Annule l’initialisation d’une instance de **ComPtr**.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtr::As, méthode](../windows/comptr-as-method.md)|Retourne un **ComPtr** objet qui représente l’interface identifiée par le paramètre de modèle spécifié.|  
|[ComPtr::AsIID, méthode](../windows/comptr-asiid-method.md)|Retourne un **ComPtr** objet qui représente l’interface identifiée par l’ID de l’interface spécifiée.|  
|[ComPtr::AsWeak, méthode](../windows/comptr-asweak-method.md)|Récupère une référence faible à l’objet actif.|  
|[ComPtr::Attach, méthode](../windows/comptr-attach-method.md)|Cela associe **ComPtr** avec le type d’interface spécifié par le paramètre de type de modèle actuel.|  
|[ComPtr::CopyTo, méthode](../windows/comptr-copyto-method.md)|Copie de l’interface actuelle ou spécifiée associée à cet **ComPtr** vers le pointeur de sortie spécifié.|  
|[ComPtr::Detach, méthode](../windows/comptr-detach-method.md)|Il dissocie **ComPtr** à partir de l’interface qu’elle représente.|  
|[ComPtr::Get, méthode](../windows/comptr-get-method.md)|Récupère un pointeur vers l’interface qui est associé à ce **ComPtr**.|  
|[ComPtr::GetAddressOf, méthode](../windows/comptr-getaddressof-method.md)|Récupère l’adresse de la [ptr_](../windows/comptr-ptr-data-member.md) membre de données, qui contient un pointeur vers l’interface représentée par ce **ComPtr**.|  
|[ComPtr::ReleaseAndGetAddressOf, méthode](../windows/comptr-releaseandgetaddressof-method.md)|Libère l’interface associée à cet **ComPtr** , puis récupère l’adresse de la [ptr_](../windows/comptr-ptr-data-member.md) membre de données, qui contient un pointeur vers l’interface qui a été publiée.|  
|[ComPtr::Reset](../windows/comptr-reset.md)|Libère toutes les références pour le pointeur vers l’interface qui est associé à ce **ComPtr**.|  
|[ComPtr::Swap, méthode](../windows/comptr-swap-method.md)|Échange l’interface gérée par l’actuel **ComPtr** avec l’interface gérée par le **ComPtr**.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtr::InternalAddRef, méthode](../windows/comptr-internaladdref-method.md)|Incrémente le décompte de références de l’interface associée à cet **ComPtr**.|  
|[ComPtr::InternalRelease, méthode](../windows/comptr-internalrelease-method.md)|Effectue une opération de libération de COM sur l’interface associée à cet **ComPtr**.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType, opérateur](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|Indique ou non un **ComPtr** gère la durée de vie d’une interface.|  
|[ComPtr::operator&, opérateur](../windows/comptr-operator-ampersand-operator.md)|Récupère l’adresse de l’actuel **ComPtr**.|  
|[ComPtr::operator=, opérateur](../windows/comptr-operator-assign-operator.md)|Assigne une valeur à actuel **ComPtr**.|  
|[ComPtr::operator->, opérateur](../windows/comptr-operator-arrow-operator.md)|Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.|  
|[ComPtr::operator==, opérateur](../windows/comptr-operator-equality-operator.md)|Indique si deux **ComPtr** objets sont égaux.|  
|[ComPtr::operator!=, opérateur](../windows/comptr-operator-inequality-operator.md)|Indique si deux **ComPtr** objets ne sont pas égaux.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[ComPtr::ptr_, données de membre](../windows/comptr-ptr-data-member.md)|Contient un pointeur vers l’interface qui est associé et géré par ce **ComPtr**.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ComPtr`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)