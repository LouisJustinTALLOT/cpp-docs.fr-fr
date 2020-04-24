---
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
ms.openlocfilehash: d0822dfc730cbbb64f8364e6fa8fe8bc7207f9f9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750744"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Microsoft Spécifique**

Attache un `VARIANT` objet dans **l’objet _variant_t.**

## <a name="syntax"></a>Syntaxe

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Objet `VARIANT` à attacher à cet objet **_variant_t.**

## <a name="remarks"></a>Notes

Prend possession `VARIANT` de la encapsulant. Cette fonction membre libère tout `VARIANT`existant encapsulé, puis copie le fourni `VARIANT`, et définit son `VARTYPE` à VT_EMPTY pour s’assurer que ses ressources ne peuvent être libérés par le destructeur **_variant_t.**

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
