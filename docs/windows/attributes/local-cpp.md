---
title: local (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: 853331ce191f8fe41d5967d2d625a3dac8543a4d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514415"
---
# <a name="local-c"></a>local (C++)

Lorsqu’il est utilisé dans l’en-tête d’interface, vous permet d’utiliser le compilateur MIDL comme générateur d’en-tête. En cas d’utilisation dans une fonction individuelle, désigne une procédure locale pour laquelle aucun stub n’est généré.

## <a name="syntax"></a>Syntaxe

```cpp
[local]
```

## <a name="remarks"></a>Notes

L’attribut **local** C++ a les mêmes fonctionnalités que l’attribut MIDL [local](/windows/win32/Midl/local) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **local**, consultez [call_as](call-as.md) .

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|`dispinterface`|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[call_as](call-as.md)