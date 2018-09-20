---
title: no_injected_text | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2cd7288b4475197d9980aab2eb9037419304c0fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442927"
---
# <a name="noinjectedtext"></a>no_injected_text

Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.

## <a name="syntax"></a>Syntaxe

```cpp
[ no_injected_text(
   boolean
) ];
```

### <a name="parameters"></a>Paramètres

*Valeur booléenne*<br/>
(Facultatif) **true** si vous ne souhaitez aucun code injecté, **false** pour permettre au code à injecter. **true** est la valeur par défaut.

## <a name="remarks"></a>Notes

L’utilisation la plus courante de la **no_injected_text** attribut C++ est par la [/Fx](../build/reference/fx-merge-injected-code.md) option du compilateur, qui insère les **no_injected_text** attribut dans le fichier .mrg.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](../windows/compiler-attributes.md)  