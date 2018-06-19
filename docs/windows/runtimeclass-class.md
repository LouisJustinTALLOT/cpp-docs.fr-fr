---
title: Runtimeclass, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26c3542f5bea21d1b705cd3253e6828ff73677df
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889005"
---
# <a name="runtimeclass-class"></a>RuntimeClass, classe
Représente une classe WinRT ou COM qui hérite des interfaces spécifiées et fournit le Windows Runtime spécifié, le COM classique et la prise en charge de la référence faible.  
  
Cette classe fournit l’implémentation standard de classes WinRT et COM, qui fournit l’implémentation de `QueryInterface`, `AddRef`, `Release` etc., gère le décompte de références du module et prend en charge la fourniture de la fabrique de classe pour objets avec activation.
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
#### <a name="parameters"></a>Paramètres  
 `classFlags`  
Paramètre facultatif. Une combinaison d’une ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valeurs d’énumération. Le `__WRL_CONFIGURATION_LEGACY__` (macro) peut être définie pour modifier la valeur par défaut de classFlags pour toutes les classes d’exécution dans le projet. S’il est défini, les instances de RuntimeClass sont non agiles par défaut. Quand ne pas défini, les instances de RuntimeClass sont agiles par défaut. Pour éviter toute ambiguïté toujours spécifier le Microsoft::WRL::FtmBase dans `TInterfaces` ou RuntimeClassType::InhibitFtmBase. Notez que, si InhibitFtmBase et FtmBase sont que tous deux utilisés de l’objet sera agile.
 
 `TInterfaces`  
La liste des interfaces implémentées par l’objet au-delà de IUnknown, IInspectable ou autres interfaces contrôlées par [RuntimeClassType](../windows/runtimeclasstype-enumeration.md). Il peut également répertorier les autres classes d’être dérivé, notamment Microsoft::WRL::FtmBase pour rendre l’objet agile et la faire implémenter IMarshal.
  
## <a name="members"></a>Membres  
`RuntimeClassInitialize` Une fonction qui initialise l’objet si la makeandinitialize, fonction de modèle est utilisée pour construire l’objet. Il retourne S_OK si l’objet a été correctement initialisé, ou un code d’erreur COM en cas d’échec de l’initialisation. Le code d’erreur COM est propagé sous la valeur de retour de MakeAndInitialize. Notez que la méthode RuntimeClassInitialize n’est pas appelée si la fonction de création de modèle est utilisée pour construire l’objet.

### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass, constructeur](../windows/runtimeclass-runtimeclass-constructor.md)|Initialise l’instance actuelle de la classe RuntimeClass.|  
|[RuntimeClass::~RuntimeClass, destructeur](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Désinitialise l’instance actuelle de la classe RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
Il s’agit d’un détail d’implémentation.
  
## <a name="requirements"></a>Spécifications  
**En-tête :** implements.h  
  
**Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)
