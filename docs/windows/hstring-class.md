---
title: Hstring, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8544a78fdbdab19f44081853f5f5878f980cec01
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879369"
---
# <a name="hstring-class"></a>HString, classe
Une classe d’assistance pour la gestion de la durée de vie de HSTRING utilisant le modèle RAII.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>Notes  
 Le Windows Runtime fournit l’accès aux chaînes par des handles HSTRING. La classe HString fournit les fonctions de commodité et d’opérateurs pour simplifier l’utilisation des handles HSTRING. Cette classe peut gérer la durée de vie de la HSTRING il détient via un modèle RAII. 
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[HString::HString, constructeur](../windows/hstring-hstring-constructor.md)|Initialise une nouvelle instance de la classe HString.|  
|[HString::~HString, destructeur](../windows/hstring-tilde-hstring-destructor.md)|Détruit l’instance actuelle de la classe HString.|  
  
### <a name="members"></a>Membres  
  
|Nom|Description|  
|----------|-----------------|  
|[HString::Set, méthode](../windows/hstring-set-method.md)|Définit la valeur de l’objet HString actuel à la chaîne à caractères larges spécifié ou le paramètre de HString.|  
|[HString::Attach, méthode](../windows/hstring-attach-method.md)|Associe l’objet HString spécifié à l’objet HString en cours.|  
|[HString::CopyTo, méthode](../windows/hstring-copyto-method.md)|Copie le HString en cours de l’objet à un objet HSTRING.|  
|[HString::Detach, méthode](../windows/hstring-detach-method.md)|Dissocie l’objet HString spécifié à partir de sa valeur sous-jacente.|  
|[HString::GetAddressOf, méthode](../windows/hstring-getaddressof-method.md)|Récupère un pointeur vers le handle HSTRING sous-jacent.|  
|[HString::Get, méthode](../windows/hstring-get-method.md)|Récupère la valeur du handle HSTRING sous-jacent.|  
|[HString::Release, méthode](../windows/hstring-release-method.md)|Supprime la valeur de chaîne sous-jacente et initialise l’objet HString en cours d’une valeur vide.|  
|[HString::MakeReference, méthode](../windows/hstring-makereference-method.md)|Crée un objet HStringReference à partir d’un paramètre de chaîne spécifiée.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[HString::Operator=, opérateur](../windows/hstring-operator-assign-operator.md)|Déplace la valeur d’un autre objet HString à l’objet HString actuel.|  
|[HString::Operator==, opérateur](../windows/hstring-operator-equality-operator.md)|Indique si les deux paramètres sont égaux.|  
|[HString::Operator!=, opérateur](../windows/hstring-operator-inequality-operator.md)|Indique si les deux paramètres ne sont pas égales.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `HString`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)