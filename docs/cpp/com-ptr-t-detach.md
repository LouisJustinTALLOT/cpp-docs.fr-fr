---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: 8ba42f19e3474cc4a3199771f761b021221f430e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190012"
---
# <a name="_com_ptr_tdetach"></a>_com_ptr_t::Detach

**Section spécifique de Microsoft**

Extrait et retourne le pointeur d'interface encapsulé.

## <a name="syntax"></a>Syntaxe

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Notes

Extrait et retourne le pointeur d'interface encapsulé, puis efface le stockage du pointeur encapsulé en lui affectant la valeur NULL. Cela supprime le pointeur d'interface de l'encapsulation. Il vous revient d’appeler `Release` sur le pointeur d’interface retourné.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
