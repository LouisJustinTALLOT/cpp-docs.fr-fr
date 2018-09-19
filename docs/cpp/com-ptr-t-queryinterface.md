---
title: _com_ptr_t::QueryInterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0add1d8f3fc73f78cee3e10642d7b5a12968a6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106870"
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