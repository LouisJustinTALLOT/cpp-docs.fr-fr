---
description: 'En savoir plus sur : _com_ptr_t :: Release'
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: a1b81295ab249b1826ea6d373f782d91765df3b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344716"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Spécifique à Microsoft**

Appelle la fonction membre **Release** de `IUnknown` sur le pointeur d’interface encapsulé.

## <a name="syntax"></a>Syntaxe

```cpp
void Release( );
```

## <a name="remarks"></a>Notes

Appelle `IUnknown::Release` sur le pointeur d’interface encapsulé, déclenchant une `E_POINTER` erreur si ce pointeur d’interface est null.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_ptr_t](../cpp/com-ptr-t-class.md)
