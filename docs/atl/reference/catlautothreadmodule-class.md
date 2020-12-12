---
description: 'En savoir plus sur : CAtlAutoThreadModule, classe'
title: CAtlAutoThreadModule, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: d1742488cca84dccfa53753bec40f9081d77f67d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165054"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule, classe

Cette classe implémente un serveur COM de modèle cloisonné et à pool de threads.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Notes

`CAtlAutoThreadModule` dérive de [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) et implémente un serveur com de modèle cloisonné et à pool de threads. `CAtlAutoThreadModule` utilise [CComApartment](../../atl/reference/ccomapartment-class.md) pour gérer un cloisonnement pour chaque thread dans le module.

Vous devez utiliser la macro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) dans la définition de classe de votre objet pour spécifier [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) comme fabrique de classe. Vous devez ensuite ajouter une seule instance d’une classe dérivée de `CAtlAutoThreadModuleT` , telle que `CAtlAutoThreadModule` . Par exemple :

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> Cette classe remplace la classe [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) obsolète.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="see-also"></a>Voir aussi

[CAtlAutoThreadModuleT, classe](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[IAtlAutoThreadModule, classe](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
