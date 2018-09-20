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
ms.openlocfilehash: c5163ea5922141faf0c4b28deb147672938997a1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375424"
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

*index*<br/>
Pointeur vers un champ qui contient une valeur d’index de base zéro.

*IID*<br/>
Tableau d’ID d’interface.

## <a name="remarks"></a>Notes

Attribue l’ID de l’interface de `Base` à l’élément de tableau spécifié par l’argument d’index.

Contrairement au nom de cette API, élément de tableau qu’une seule est modifiée ; pas l’intégralité du tableau.

Pour plus d’informations sur `Base`, consultez la section Typedefs publics dans [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[InterfaceTraits, structure](../windows/interfacetraits-structure.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)