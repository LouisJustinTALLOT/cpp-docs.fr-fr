---
description: 'En savoir plus sur : no_injected_text'
title: no_injected_text (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 3d6b4b77055b6706256b25b0b722034e0275ec19
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327470"
---
# <a name="no_injected_text"></a>no_injected_text

Empêche le compilateur d’injecter du code en raison de l’utilisation d’un attribut.

## <a name="syntax"></a>Syntaxe

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Paramètres

*boolean*<br/>
(Facultatif) **`true`** Si vous ne souhaitez pas injecter de code, **`false`** pour autoriser l’injection de code. **`true`** est la valeur par défaut.

## <a name="remarks"></a>Notes

L’utilisation la plus courante de l’attribut **no_injected_text** C++ est l’option du compilateur [/FX](../../build/reference/fx-merge-injected-code.md) , qui insère l’attribut **no_injected_text** dans le fichier. mrg.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)
