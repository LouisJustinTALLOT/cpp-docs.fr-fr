---
description: 'En savoir plus sur les éléments suivants : HelpString'
title: HelpString (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 3b3aa2470080f33fd4a9dea4f063e908c0431d5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148809"
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

L’attribut C++ **helpString** a les mêmes fonctionnalités que l’attribut MIDL [helpString](/windows/win32/Midl/helpstring) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [DefaultValue](defaultvalue.md) pour obtenir un exemple d’utilisation de **helpString**.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**, **`typedef`** , **`class`** , méthode, propriété|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)
