---
title: no_injected_text (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 354643020e704a87daa2e56e923b6a0a704bf0b5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038367"
---
# <a name="noinjectedtext"></a>no_injected_text

Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.

## <a name="syntax"></a>Syntaxe

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Paramètres

*boolean*<br/>
(Facultatif) **true** si vous ne souhaitez aucun code injecté, **false** pour permettre au code à injecter. **true** est la valeur par défaut.

## <a name="remarks"></a>Notes

L’utilisation la plus courante de la **no_injected_text** attribut C++ est par la [/Fx](../../build/reference/fx-merge-injected-code.md) option du compilateur, qui insère les **no_injected_text** attribut dans le fichier .mrg.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)