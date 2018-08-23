---
title: Interfacetraits::fillarraywithiid, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fc4679d9e6d3a4fdfc112d8a8b471ceb2646ecc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583726"
---
# <a name="interfacetraitsfillarraywithiid-method"></a>InterfaceTraits::FillArrayWithIid, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*  
Pointeur vers un champ qui contient une valeur d’index de base zéro.

*IID*  
Tableau d’ID d’interface.

## <a name="remarks"></a>Notes

Attribue l’ID de l’interface de `Base` à l’élément de tableau spécifié par l’argument d’index.

Contrairement au nom de cette API, élément de tableau qu’une seule est modifiée ; pas l’intégralité du tableau.

Pour plus d’informations sur `Base`, consultez la section Typedefs publics dans [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[InterfaceTraits, structure](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)