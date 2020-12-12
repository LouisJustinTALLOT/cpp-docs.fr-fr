---
description: 'En savoir plus sur : _com_ptr_t ::D Etach'
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: ec2a18a04b8c32e373225235fd0d6f520e768af0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295508"
---
# <a name="_com_ptr_tdetach"></a>_com_ptr_t::Detach

**Spécifique à Microsoft**

Extrait et retourne le pointeur d'interface encapsulé.

## <a name="syntax"></a>Syntaxe

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Notes

Extrait et retourne le pointeur d'interface encapsulé, puis efface le stockage du pointeur encapsulé en lui affectant la valeur NULL. Cela supprime le pointeur d'interface de l'encapsulation. C’est à vous d’appeler `Release` sur le pointeur d’interface retourné.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_ptr_t](../cpp/com-ptr-t-class.md)
