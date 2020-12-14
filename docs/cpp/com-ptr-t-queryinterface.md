---
description: 'En savoir plus sur : _com_ptr_t :: QueryInterface'
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 6c6ff19227c920aade762af295942d8058a17ad3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295339"
---
# <a name="_com_ptr_tqueryinterface"></a>_com_ptr_t::QueryInterface

**Spécifique à Microsoft**

Appelle la fonction membre **QueryInterface** de `IUnknown` sur le pointeur d’interface encapsulé.

## <a name="syntax"></a>Syntaxe

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>Paramètres

*vaut*<br/>
`IID` d’un pointeur d’interface.

*p*<br/>
Pointeur d'interface brut.

## <a name="remarks"></a>Notes

Appelle `IUnknown::QueryInterface` sur le pointeur d’interface encapsulé avec le spécifié `IID` et retourne le pointeur d’interface brut résultant dans *p*. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_ptr_t](../cpp/com-ptr-t-class.md)
