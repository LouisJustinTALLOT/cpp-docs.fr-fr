---
title: CAtlAutoThreadModule, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 882a32b1a9f08f3fd07f1d53d508b101c5500f5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037057"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule, classe

Cette classe implémente un serveur COM mis en pool de thread, le modèle de cloisonnement.

> [!IMPORTANT]
> Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Notes

`CAtlAutoThreadModule` dérive de [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) et implémente un serveur COM mis en pool de thread, le modèle de cloisonnement. `CAtlAutoThreadModule` utilise [CComApartment](../../atl/reference/ccomapartment-class.md) pour gérer un cloisonnement pour chaque thread dans le module.

Vous devez utiliser le [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) macro dans la définition de classe de votre objet pour spécifier [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) car la fabrique de classe. Vous devez ensuite ajouter une seule instance d’une classe dérivée de `CAtlAutoThreadModuleT` comme `CAtlAutoThreadModule`. Exemple :

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> Cette classe remplace obsolète [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

## <a name="see-also"></a>Voir aussi

[CAtlAutoThreadModuleT, classe](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[IAtlAutoThreadModule, classe](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
