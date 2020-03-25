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
ms.openlocfilehash: 3792ed4d0fcd86c4a4e846771c450413fda130b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187763"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Section spécifique de Microsoft**

Attache un objet `VARIANT` dans l’objet **_variant_t** .

## <a name="syntax"></a>Syntaxe

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Objet `VARIANT` à attacher à cet objet **_variant_t** .

## <a name="remarks"></a>Notes

Prend possession de l' `VARIANT` en l’encapsulant. Cette fonction membre libère les `VARIANT`encapsulés existants, puis copie le `VARIANT`fourni et définit ses `VARTYPE` sur VT_EMPTY pour s’assurer que ses ressources peuvent être libérées uniquement par le destructeur **_variant_t** .

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)
