---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 42953c92e4cf31b5ccd02dd51811fc1fdeedbcaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543830"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface

**Section spécifique à Microsoft**

Appelle le **QueryInterface** fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.

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

*IID*<br/>
`IID` d’un pointeur d’interface.

*p*<br/>
Pointeur d'interface brut.

## <a name="remarks"></a>Notes

Appels `IUnknown::QueryInterface` sur le pointeur d’interface encapsulé avec la valeur `IID` et retourne le pointeur d’interface brut résultant dans *p*. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)