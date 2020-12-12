---
description: 'En savoir plus sur : _variant_t :: Attach'
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: de13b1e8138eb24971e52165ee84fc92d97ca3d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116650"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Spécifique à Microsoft**

Attache un `VARIANT` objet dans l’objet **_variant_t** .

## <a name="syntax"></a>Syntaxe

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Paramètres

*varSrc*<br/>
`VARIANT`Objet à attacher à cet objet **_variant_t** .

## <a name="remarks"></a>Notes

Prend possession du `VARIANT` en l’encapsulant. Cette fonction membre libère tout encapsulé existant `VARIANT` , puis copie le fourni `VARIANT` et définit son `VARTYPE` VT_EMPTY pour s’assurer que ses ressources peuvent être libérées uniquement par le destructeur de **_variant_t** .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
