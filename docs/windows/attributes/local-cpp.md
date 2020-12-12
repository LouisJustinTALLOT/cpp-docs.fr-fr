---
description: 'En savoir plus sur : local (C++)'
title: local (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: 7fa1366b78576224f8fcc0d91392fe1fc6cb8af9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327511"
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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|`dispinterface`|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[call_as](call-as.md)
