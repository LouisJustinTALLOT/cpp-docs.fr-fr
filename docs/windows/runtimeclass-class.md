---
title: Runtimeclass, classe | Microsoft Docs
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
ms.openlocfilehash: 7f76695cfe3dcad0f5c835577aa4cc9b7cd3ec62
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017641"
---
# <a name="runtimeclass-class"></a>RuntimeClass, classe
Représente une classe WinRT ou COM qui hérite des interfaces spécifiées et fournit le Runtime Windows spécifié, COM classique et prise en charge de la référence faible.  
  
Cette classe fournit l’implémentation de code réutilisable de classes COM et WinRT, qui fournit l’implémentation de `QueryInterface`, `AddRef`, `Release` etc., gère le décompte de références du module et prend en charge en fournissant la fabrique de classe pour objets pouvant être activés.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
### <a name="parameters"></a>Paramètres  
 *classFlags*  
Paramètre facultatif. Une combinaison d’une ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valeurs d’énumération. Le `__WRL_CONFIGURATION_LEGACY__` macro peut être définie pour modifier la valeur par défaut classFlags pour toutes les classes de runtime dans le projet. S’il est défini, les instances de RuntimeClass sont non agiles par défaut. Lorsque ne pas défini, RuntimeClass instances sont agiles par défaut. Pour éviter toute ambiguïté toujours spécifier le `Microsoft::WRL::FtmBase` dans `TInterfaces` ou `RuntimeClassType::InhibitFtmBase`. Notez que, si InhibitFtmBase et FtmBase sont que tous deux utilisés de l’objet sera agile.
 
 *TInterfaces*  
La liste des interfaces de l’objet implémente au-delà `IUnknown`, `IInspectable` ou d’autres interfaces contrôlés par [RuntimeClassType](../windows/runtimeclasstype-enumeration.md). Il peut également répertorier les autres classes à être dérivé, notamment `Microsoft::WRL::FtmBase` pour rendre l’objet agile et le rendre implémenter `IMarshal`.
  
## <a name="members"></a>Membres  
`RuntimeClassInitialize` Une fonction qui initialise l’objet si le `MakeAndInitialize` fonction de modèle est utilisée pour construire l’objet. Elle retourne S_OK si l’objet a été correctement initialisé, ou un code d’erreur COM en cas d’échec de l’initialisation. Le code d’erreur COM est propagé en tant que valeur de retour de `MakeAndInitialize`. Notez que le `RuntimeClassInitialize` méthode n’est pas appelée si le `Make` fonction de modèle est utilisée pour construire l’objet.

### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass, constructeur](../windows/runtimeclass-runtimeclass-constructor.md)|Initialise l’instance actuelle de la classe RuntimeClass.|  
|[RuntimeClass::~RuntimeClass, destructeur](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Annule l’initialisation de l’instance actuelle de la classe RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
Il s’agit d’un détail d’implémentation.
  
## <a name="requirements"></a>Configuration requise  
**En-tête :** implements.h  
  
**Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)