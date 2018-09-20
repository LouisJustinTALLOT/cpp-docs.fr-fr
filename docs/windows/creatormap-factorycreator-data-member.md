---
title: Creatormap::FactoryCreator, données de membre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
dev_langs:
- C++
helpviewer_keywords:
- factoryCreator data member
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 12d4fdd415ab37c9af0b0b34651e7cd2f00cf31b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405279"
---
# <a name="creatormapfactorycreator-data-member"></a>CreatorMap::factoryCreator, données de membre

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Paramètres

*currentflags*<br/>
Parmi les [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérateurs.

*entry*<br/>
Un CreatorMap.

*iidClassFactory*<br/>
L’ID d’interface d’une fabrique de classe.

*fabrique*<br/>
Lorsque l’opération terminée, l’adresse d’une fabrique de classe.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Crée une fabrique pour la CreatorMap spécifié.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[CreatorMap, structure](../windows/creatormap-structure.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)