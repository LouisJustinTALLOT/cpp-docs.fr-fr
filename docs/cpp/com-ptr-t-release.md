---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: f455e855e782a939e79898ee46e445f65d25d37a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170590"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Section spécifique de Microsoft**

Appelle la fonction membre **Release** de `IUnknown` sur le pointeur d’interface encapsulé.

## <a name="syntax"></a>Syntaxe

```
void Release( );
```

## <a name="remarks"></a>Notes

Appelle `IUnknown::Release` sur le pointeur d’interface encapsulé, en déclenchant une erreur de `E_POINTER` si ce pointeur d’interface a la valeur NULL.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
