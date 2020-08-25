---
title: local (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: dea62653478e451af00fa47b72984f3b580aadc0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834087"
---
# <a name="local-c"></a>local (C++)

Lorsqu’il est utilisé dans l’en-tête d’interface, vous permet d’utiliser le compilateur MIDL comme générateur d’en-tête. En cas d’utilisation dans une fonction individuelle, désigne une procédure locale pour laquelle aucun stub n’est généré.

## <a name="syntax"></a>Syntaxe

```cpp
[local]
```

## <a name="remarks"></a>Notes

L’attribut C++ **local** a les mêmes fonctionnalités que l’attribut MIDL [local](/windows/win32/Midl/local) .

## <a name="example"></a>Exemple

Consultez [call_as](call-as.md) pour obtenir un exemple d’utilisation de **local**.

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**, méthode d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|`dispinterface`|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[call_as](call-as.md)
