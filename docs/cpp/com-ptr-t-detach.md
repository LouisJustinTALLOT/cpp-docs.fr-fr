---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154959"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Section spécifique à Microsoft**

Extrait et retourne le pointeur d'interface encapsulé.

## <a name="syntax"></a>Syntaxe

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Notes

Extrait et retourne le pointeur d’interface encapsulé, puis efface le stockage du pointeur encapsulé avec la valeur NULL. Cela supprime le pointeur d'interface de l'encapsulation. Il vous incombe d’appeler `Release` sur le pointeur d’interface retourné.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)