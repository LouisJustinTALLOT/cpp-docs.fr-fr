---
title: HelpString (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: d22ecf5a7131a1368abf2b1fbd8261ec6195b51e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166963"
---
# <a name="helpstring"></a>helpstring

Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>Paramètres

*string*<br/>
Texte de la chaîne d’aide.

## <a name="remarks"></a>Notes

L’attribut **helpString** C++ a les mêmes fonctionnalités que l’attribut MIDL de [helpString](/windows/win32/Midl/helpstring) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [DefaultValue](defaultvalue.md) pour obtenir un exemple d’utilisation de **helpString**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **typedef**, **classe**, méthode, propriété|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)
