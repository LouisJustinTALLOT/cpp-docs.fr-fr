---
title: no_injected_text (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 5f98be3478b2e1eeb4b464f1784f3f4ece22d8a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166612"
---
# <a name="no_injected_text"></a>no_injected_text

Empêche le compilateur d’injecter du code en raison de l’utilisation d’un attribut.

## <a name="syntax"></a>Syntaxe

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Paramètres

*boolean*<br/>
Facultatif **true** si vous ne souhaitez pas que le code soit injecté, **false** pour autoriser l’injection du code. la valeur par défaut est **true** .

## <a name="remarks"></a>Notes

L’utilisation la plus courante de l’attribut **no_injected_text** C++ est l’option du compilateur [/FX](../../build/reference/fx-merge-injected-code.md) , qui insère l’attribut **no_injected_text** dans le fichier. mrg.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)
