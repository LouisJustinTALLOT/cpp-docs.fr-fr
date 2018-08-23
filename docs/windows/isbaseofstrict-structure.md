---
title: IsBaseOfStrict (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e20748f1929a00084b0fb7bf16342e48e16a82b2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610123"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename Base,
   typename Derived
>

struct IsBaseOfStrict;
template <
   typename Base
>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Paramètres

*base de*  
Type de base.

*DÉRIVÉS*  
Le type dérivé.

## <a name="remarks"></a>Notes

Teste si un type est la base d'un autre.

Le premier modèle teste si un type est dérivé d’un type de base, ce qui peut produire **true** ou **false**. Le deuxième modèle teste si un type est dérivé lui-même, ce qui entraîne toujours une valeur **false**.

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[IsBaseOfStrict::value, constante](../windows/isbaseofstrict-value-constant.md)|Indique si un type est la base d’un autre.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IsBaseOfStrict`

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)